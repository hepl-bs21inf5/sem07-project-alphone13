<script setup lang="ts">
import QuestionRadio from '@/components/QuestionRadio.vue'
import { QuestionState } from '@/utils/models'
import { reactive, ref, computed } from 'vue'

const questions = ref<
  {
    question: string
    correct_answer: string
    incorrect_answers: string[]
  }[]
>([])
//Il faut que j'adapte en fontion de TRivia et non comme dans QuizForm
const submitted = computed<boolean>(() =>
  questionStates.value.every(
    (state) => state === QuestionState.Correct || state === QuestionState.Wrong,
  ),
)
const answers = reactive<{ [key: number]: string | null }>({})
const checkedNames = ref<string[]>([])
const questionStates = ref<QuestionState[]>([])

const filled = computed<boolean>(() =>
  questionStates.value.every((state) => state === QuestionState.Fill),
)
const score = computed<number>(
  () => questionStates.value.filter((state) => state === QuestionState.Correct).length,
)
const totalScore = computed<number>(() => questionStates.value.length)
/*pour faire comme dans Quizform avec les message de félicitations */

function submit(event: Event): void {
  // fait des comparaison valeur vide-pleine
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Submit) //envoie les réponses rentrées par l'utilisateur
}

function reset(event: Event): void {
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Empty) //on met l'état des réponses à vide.
}

fetch('https://opentdb.com/api.php?amount=10&type=multiple')
  .then((response) => response.json())
  .then((data) => (questions.value = data.results))
</script>

<template>
  <form>
    <QuestionRadio
      v-for="(question, index) in questions"
      :id="index.toString()"
      :key="index"
      :submitted="submitted"
      answer="answers[index]"
      :text="question.question"
      :options="[
        { value: question.correct_answer, text: question.correct_answer },
        ...question.incorrect_answers.map((answer) => ({
          value: answer,
          text: answer,
        })),
      ]"
    /><!--j'ai ajouté le submitted pour que ça puisse envoyer la réponse et qu'elle soit vérifiée-->
  </form>
  <div>Réponses correctes : {{ questionStates }}</div>

  <button class="btn btn-primary" :class="{ disabled: !filled }" @click="submit">Terminer</button>

  <button class="btn btn-primary" @click="reset">Réinitialiser</button>

  <div>Score : {{ score }} / {{ totalScore }}</div>
  <div>Debug états : {{ questionStates }}</div>
</template>
