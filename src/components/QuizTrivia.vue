<script setup lang="ts">
import QuestionRadio from '@/components/QuestionRadio.vue'
import { QuestionState } from '@/utils/models'
import { reactive, ref } from 'vue'

const questions = ref<
  {
    question: string
    correct_answer: string
    incorrect_answers: string[]
  }[]
>([])
const answers = reactive<{ [key: number]: string | null }>({})

/*const checkedNames = ref<string[]>([])
const questionStates = ref<QuestionState[]>([])
const filled = computed<boolean>(() =>
  questionStates.value.every((state) => state === QuestionState.Fill),
) /*pour faire comme dans Quizform avec les message de félicitations */

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
      answer=""
      :text="question.question"
      :options="[
        { value: question.correct_answer, text: question.correct_answer },
        ...question.incorrect_answers.map((answer) => ({
          value: answer,
          text: answer,
        })),
      ]"
    />
  </form>
  <!--<div>Réponses correctes : {{ questionStates }}</div>

<button class="btn btn-primary" :class="{ disabled: !filled }" @click="submit">Terminer</button>
</form>
<button class="btn btn-primary" @click="reset">Réinitialiser</button>

<div>Score : {{ score }} / {{ totalScore }}</div>
<div>Debug états : {{ questionStates }}</div>-->
</template>
