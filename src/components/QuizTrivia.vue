<script setup lang="ts">
import { computed, ref } from 'vue'
import QuestionRadio from './Questionradio.vue'

// Définition des états possibles pour une question
enum QuestionState {
  Empty = 'Empty', // Pas encore répondu
  Fill = 'Fill', // Réponse donnée
  Correct = 'Correct', // Bonne réponse
  Wrong = 'Wrong',
  Submit = "Submit", // Mauvaise réponse
}

// Questions et états des réponses
const questions = ref<
  {
    question: string
    correct_answer: string
    incorrect_answers: string[]
    shuffledAnswers: { value: string; text: string }[]
  }[]
>([])
const questionStates = ref<QuestionState[]>([])

// Gestion des boutons
const filled = computed(() => questionStates.value.every((state) => state === QuestionState.Fill))

const submitted = computed(() =>
  questionStates.value.every(
    (state) => state === QuestionState.Correct || state === QuestionState.Wrong,
  ),
)

// Calcul du score
const score = computed<number>(
  () => questionStates.value.filter((state) => state === QuestionState.Correct).length,
)
const totalScore = computed<number>(() => questionStates.value.length)

// Mélanger les réponses
function shuffleArray<T>(array: T[]): T[] {
  return array.sort(() => Math.random() - 0.5)
}

// Charger les questions au démarrage
fetchQuestions()

// Charger de nouvelles questions
function fetchQuestions(): void {
  questions.value = []
  questionStates.value = [] // Réinitialiser les états
  fetch('https://opentdb.com/api.php?amount=10&type=multiple')
    .then((response) => response.json())
    .then((data) => {
      questions.value = data.results.map(
        (q: { correct_answer: unknown; incorrect_answers: unknown[] }) => ({
          ...q,
          shuffledAnswers: shuffleArray([
            { value: q.correct_answer, text: q.correct_answer },
            ...q.incorrect_answers.map((answer: unknown) => ({
              value: answer,
              text: answer,
            })),
          ]),
        }),
      )
      // Initialiser tous les états à "Empty"
      questionStates.value = new Array(data.results.length).fill(QuestionState.Empty)
    })
}

// Soumettre le quiz

function reset(event: Event): void {
  event.preventDefault();
  questionStates.value = questionStates.value.map(() => QuestionState.Empty);
}

function submit(event: Event): void {
  event.preventDefault();
  questionStates.value = questionStates.value.map(() => QuestionState.Submit);
}

</script>

<template>
  <form>
    <div v-for="(question, index) in questions" :key="index">
      <QuestionRadio
        :id="index.toString()"
        v-model="questionStates[index]"
        :text="question.question"
        :answer="question.correct_answer"
        :options="question.shuffledAnswers"
      />
    </div>

    <div class="buttons">
      <!-- Bouton Terminer -->
      <button class="btn btn-primary" :disabled="!filled" type="button" @click="submit">
        Terminer
      </button>

      <!-- Bouton Réinitialiser -->
      <button class="btn btn-secondary" type="button" @click="reset">Réinitialiser</button>

      <!-- Bouton Nouvelles questions -->
      <button class="btn btn-info" type="button" @click="fetchQuestions">
        Nouvelles questions
      </button>
    </div>

    <!-- Affichage du score -->
    <div v-if="submitted" class="score">
      <p>Votre score : {{ score }} / {{ totalScore }}</p>
    </div>
  </form>
</template>

<style scoped>
.text-danger {
  color: rgb(128, 0, 0) !important;
}
.text-success {
  color: rgb(196, 34, 196) !important;
}

</style>
