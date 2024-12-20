<script setup lang="ts">
import { computed, ref } from 'vue'
import QuestionRadio from '@/components/QuestionRadio.vue'
import QuestionText from './QuestionText.vue'
import { QuestionState } from '@/utils/models'
import QuestionCheckbox from './QuestionCheckbox.vue'

const checkedNames = ref<string[]>([])
const questionStates = ref<QuestionState[]>([])
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
    <p>&nbsp;</p>
    <!--ça importe ce qu'il y a dans le questiontext. permet de faire une réponse libre-->
    <QuestionText
      id="exampleFormControlInput"
      v-model="questionStates[1]"
      text=" Combien de pattes a un chat ?"
      placeholder="Veuillez saisir une réponse"
      answer-detail="Le chat est un mammifère quadrupède, donc un animal à quatre pattes."
      :answer="['4', 'quatre', 'Quatre', 'Un quadripède']"
    />
    <p>&nbsp;</p>
    <QuestionRadio
      id="calcul"
      v-model="questionStates[2]"
      answer="10"
      answer-detail="Il suffit d'additionner 2+3=5, puis de faire 5+5 et on trouve 10."
      text=" Combien font 2+3+5 ?"
      :options="[
        { value: '10', text: '10' },
        { value: '9', text: '9' },
        { value: '12', text: '12' },
      ]"
    />
    <p>&nbsp;</p>
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
    <!-- Ajoute une ligne vide -->

    <QuestionRadio
      id="eiffel"
      v-model="questionStates[3]"
      answer="Paris"
      answer-detail="La Tour-Eiffel se trouve dans le 7ᵉ arrondissement, sur le Champ-de-Mars, près de la Seine."
      text=" Où se trouve la Tour-Eiffel ?"
      :options="[
        { value: 'Oslo', text: 'Oslo' },
        { value: 'Sydney', text: 'Sydney' },
        { value: 'Paris', text: 'Paris' },
      ]"
    />
    <div>Réponses correctes : {{ questionStates }}</div>
  </form>
  <button class="btn btn-primary" :class="{ disabled: !filled }" @click="submit">Terminer</button>

  <button class="btn btn-primary" @click="reset">Réinitialiser</button>

  <div>Score : {{ score }} / {{ totalScore }}</div>
  <div>Debug états : {{ questionStates }}</div>
</template>
