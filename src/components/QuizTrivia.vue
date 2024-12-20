<script setup lang="ts">
import QuestionRadio from '@/components/QuestionRadio.vue'
import { QuestionState } from '@/utils/models'
import { reactive, ref, computed } from 'vue'

// Définition des questions et réponses
const questions = ref<
  {
    question: string
    correct_answer: string
    incorrect_answers: string[]
    shuffledAnswers: { value: string; text: string }[]
  }[]
>([])

const answers = reactive<{ [key: number]: string | null }>({})
const questionStates = ref<QuestionState[]>([])

// Calculs réactifs
const submitted = computed<boolean>(() =>
  questionStates.value.every(
    (state) => state === QuestionState.Correct || state === QuestionState.Wrong,
  ),
)
const filled = computed<boolean>(
  () =>
    questions.value.length > 0 && // Toutes les questions doivent être disponibles
    Object.keys(answers).length === questions.value.length && // Toutes les réponses doivent être dans le tableau
    Object.values(answers).every((answer) => answer !== null), // Toutes les réponses doivent être remplies
)
const score = computed<number>(
  () => questionStates.value.filter((state) => state === QuestionState.Correct).length,
)
const totalScore = computed<number>(() => questions.value.length)

// Mélanger un tableau
function shuffleArray<T>(array: T[]): T[] {
  return array.sort(() => Math.random() - 0.5)
}

// Récupérer les questions depuis l'API
function fetchQuestions(): void {
  fetch('https://opentdb.com/api.php?amount=10&type=multiple')
    .then((response) => response.json())
    .then((data) => {
      questions.value = data.results.map(
        (question: { correct_answer: any; incorrect_answers: any[] }) => {
          const allAnswers = [
            { value: question.correct_answer, text: question.correct_answer },
            ...question.incorrect_answers.map((answer) => ({
              value: answer,
              text: answer,
            })),
          ]
          return {
            ...question,
            shuffledAnswers: shuffleArray(allAnswers),
          }
        },
      )
      questionStates.value = new Array(questions.value.length).fill(QuestionState.Empty)
      Object.keys(answers).forEach((key) => (answers[key] = null)) // Réinitialise les réponses
    })
}

// Soumettre les réponses pour correction. les conditions servent à verifier si la réponse est juste
function submit(event: Event): void {
  event.preventDefault()
  if (!filled.value) {
    alert('Veuillez répondre à toutes les questions avant de soumettre.')
    return
  }

  questionStates.value = questions.value.map((question, index) => {
    const userAnswer = answers[index]
    if (userAnswer === question.correct_answer) {
      return QuestionState.Correct
    } else {
      return QuestionState.Wrong
    }
  })
}

// Réinitialiser uniquement les réponses utilisateur
function reset(event: Event): void {
  event.preventDefault()
  Object.keys(answers).forEach((key) => (answers[key] = null)) // Effacer toutes les réponses
  questionStates.value = new Array(questions.value.length).fill(QuestionState.Empty) // Remettre à vide
}

fetchQuestions()
</script>

<template>
  <form @submit.prevent="submit">
    <div v-for="(question, index) in questions" :key="index">
      <QuestionRadio
        :id="index.toString()"
        :submitted="submitted"
        v-model="answers[index]"
        :text="question.question"
        :options="question.shuffledAnswers"
      />
    </div>

    <!-- Boutons ne marchent pas correctement-->
    <button class="btn btn-primary" :disabled="!filled" @click="submit">Terminer</button>
    <button class="btn btn-secondary" @click="reset">Réinitialiser</button>

    <!-- Affichage du score -->
    <div v-if="submitted">
      <p>Score : {{ score }} / {{ totalScore }}</p>
      <p>Bravo ! Vous avez terminé le quiz.</p>
    </div>
  </form>
</template>
