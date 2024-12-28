<script setup lang="ts">
import { computed, ref } from 'vue'
import QuestionRadio from './Questionradio.vue'
import QuestionText from './QuestionText.vue'
import { QuestionState } from '@/utils/models'
import QuestionCheckbox from './QuestionCheckbox.vue'
import QuestionSelect from './QuestionSelect.vue'

// Déclarer les questions comme un tableau réactif
const questions = ref([
  {
    text: 'De quelle couleur est le cheval blanc de Napoléon ?',
    options: [
      { value: 'blanc', text: 'Blanc' },
      { value: 'brun', text: 'Brun' },
      { value: 'noir', text: 'Noir' },
    ],
    answer: 'blanc',
    type: 'radio',
  },
  {
    text: "Qui est le principal antagoniste de 'JoJo's Bizarre Adventure: Stardust Crusaders' ?",
    options: [
      { value: 'jotaro', text: 'Jotaro Kujo' },
      { value: 'joseph', text: 'Joseph Joestar' },
      { value: 'dio', text: 'Dio Brando' },
      { value: 'joseph', text: 'Jonathan Joestar' },
    ],
    answer: 'dio',
    type: 'select',
  },

  {
    text: 'Combien de pattes a un chat ?',
    options: [],
    answer: '4',
    type: 'text',
  },
  {
    text: 'Combien font 2+3+5 ?',
    options: [
      { value: '10', text: '10' },
      { value: '9', text: '9' },
      { value: '12', text: '12' },
    ],
    answer: '10',
    type: 'radio',
  },
  {
    text: 'Où se trouve la Tour-Eiffel ?',
    options: [
      { value: 'Oslo', text: 'Oslo' },
      { value: 'Sydney', text: 'Sydney' },
      { value: 'Paris', text: 'Paris' },
    ],
    answer: 'Paris',
    type: 'radio',
  },

  {
    text: "Comment s'appelle le Stand de Jotaro Kujo ?",
    options: [
      { value: 'StarPlatinum', text: 'Star Platinum' },
      { value: 'CrazyDiamond', text: 'Crazy Diamond' },
      { value: 'TheWorld', text: 'The World' },
    ],
    answer: 'StarPlatinum',
    type: 'select',
  },

  {
    text: 'Lesquels parmi ces jeux ne se jouent pas sur Nintendo ?',
    options: [
      { value: 'Mario Galaxy 2', text: 'Mario Galaxy 2' },
      { value: 'Pou', text: 'Pou' },
      { value: 'Talking with Tom', text: 'Talking with Tom' },
      { value: 'Paper Mario - Origami King', text: 'Paper Mario - Origami King' },
    ],
    answer: ['Pou', 'Talking with Tom'],
    type: 'checkbox',
  },
])

const questionStates = ref<QuestionState[]>(
  new Array(questions.value.length).fill(QuestionState.Empty),
)

const filled = computed<boolean>(() =>
  questionStates.value.every((state) => state === QuestionState.Fill),
)

const submitted = computed<boolean>(() =>
  questionStates.value.every(
    (state) => state === QuestionState.Correct || state === QuestionState.Wrong,
  ),
)

const score = computed<number>(
  () => questionStates.value.filter((state) => state === QuestionState.Correct).length,
)
const totalScore = computed<number>(() => questionStates.value.length)

function submit(event: Event): void {
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Submit)
}

function reset(event: Event): void {
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Empty) //on met l'état des réponses à vide.
}
</script>

<template>
  <form>
    <p>&nbsp;</p>
    <p class="question-title">Question 1</p>
    <!--Là on a modifier le v-model correct.Answer en questionStates pour que ça corresponde à une valeur réactive (ref), qu'on a définit plus haut. -->
    <QuestionRadio
      id="cheval"
      v-model="questionStates[0]"
      answer="blanc"
      answer-detail="La réponse est dans la question."
      text="De quelle couleur est le cheval blanc de Napoléon ?"
      :options="[
        { value: 'blanc', text: 'Blanc' },
        { value: 'brun', text: 'Brun' },
        { value: 'noir', text: 'Noir' },
      ]"
    />
    &nbsp;
    <p class="question-title">Question 2</p>

    <QuestionSelect
      id="question-select-jojo"
      v-model="questionStates[1]"
      text="Comment s'appelle le Stand de Jotaro Kujo ?"
      :options="[
        { value: 'StarPlatinum', text: 'Star Platinum' },
        { value: 'CrazyDiamond', text: 'Crazy Diamond' },
        { value: 'TheWorld', text: 'The World' },
      ]"
      answer="StarPlatinum"
      answer-detail="Le Stand de Jotaro Kujo s'appelle Star Platinum, connu pour sa vitesse et sa force exceptionnelles."
    />
    <p class="question-title">Question 3</p>
    &nbsp;
    <!--ça importe ce qu'il y a dans le questiontext. permet de faire une réponse libre-->
    <QuestionText
      id="exampleFormControlInput"
      v-model="questionStates[2]"
      text=" Combien de pattes a un chat ?"
      placeholder="Veuillez saisir une réponse"
      answer-detail="Le chat est un mammifère quadrupède, donc un animal à quatre pattes."
      :answer="['4', 'quatre', 'Quatre', 'Un quadripède']"
    />
    &nbsp;
    <p class="question-title">Question 4</p>

    <QuestionRadio
      id="calcul"
      v-model="questionStates[3]"
      answer="10"
      answer-detail="Il suffit d'additionner 2+3=5, puis de faire 5+5 et on trouve 10."
      text=" Combien font 2+3+5 ?"
      :options="[
        { value: '10', text: '10' },
        { value: '9', text: '9' },
        { value: '12', text: '12' },
      ]"
    />
    &nbsp;
    <p class="question-title">Question 5</p>

    <QuestionCheckbox
      id="games"
      v-model="questionStates[4]"
      text="Lesquels parmi ces jeux ne se jouent pas sur Nintendo (Plusieurs réponses possibles)"
      :submitted="submitted"
      :options="[
        { value: 'Mario Galaxy 2', text: 'Mario Galaxy 2' },
        { value: 'Pou', text: 'Pou' },
        { value: 'Talking with Tom', text: 'Talking with Tom' },
        { value: 'Paper Mario - Origami King', text: 'Paper Mario - Origami King' },
      ]"
      :answer="['Pou', 'Talking with Tom']"
      answer-detail="['Pou et Talking with Tom ne sont pas des licences Nintendo.']"
    />
    <p>&nbsp;</p>
    <p class="question-title">Question 6</p>

    <QuestionRadio
      id="eiffel"
      v-model="questionStates[5]"
      answer="Paris"
      answer-detail="La Tour-Eiffel se trouve dans le 7ᵉ arrondissement, sur le Champ-de-Mars, près de la Seine."
      text=" Où se trouve la Tour-Eiffel ?"
      :options="[
        { value: 'Oslo', text: 'Oslo' },
        { value: 'Sydney', text: 'Sydney' },
        { value: 'Paris', text: 'Paris' },
      ]"
    />
    &nbsp;
    <p class="question-title">Question 7</p>

    <QuestionSelect
      id="Jojo's Bizarre Adventure"
      v-model="questionStates[6]"
      text="Qui est le principal antagoniste de 'JoJo's Bizarre Adventure: Stardust Crusaders' ?"
      :options="[
        { value: 'jotaro', text: 'Jotaro Kujo' },
        { value: 'joseph', text: 'Joseph Joestar' },
        { value: 'dio', text: 'Dio Brando' },
        { value: 'joseph', text: 'Jonathan Joestar' },
      ]"
      answer="dio"
      answer-detail="Dio Brando est l'antagoniste principal de Stardust Crusaders. Son Stand est Tha Warudo."
    />
  </form>
  &nbsp;
  &nbsp;
  <button class="btn btn-primary" :class="{ disabled: !filled }" @click="submit">Terminer</button>
  &nbsp;
  <button class="btn btn-primary" @click="reset">Réinitialiser</button>&nbsp;
  <div class="score">Score : {{ score }} / {{ totalScore }}</div>
  &nbsp;
</template>

<style scoped>
.text-danger {
  color: rgb(239, 46, 46) !important;
}
.text-success {
  color: rgb(196, 34, 196) !important;
}
</style>
