<script setup lang="ts">
import { computed, ref } from 'vue'
import QuestionRadio from '@/components/QuestionRadio.vue'
import QuestionText from './QuestionText.vue'

const cheval = ref<string | null>(null)
const calcul = ref<string | null>(null)
const Eiffel = ref<string | null>(null)

const filled = computed<boolean>(
  () => cheval.value !== null && calcul.value !== null && Eiffel.value !== null,
) 

function submit(event: Event): void {
  event.preventDefault()
  let score: number = 0
  if (cheval.value === 'blanc') {
    score += 1
  }

  if (calcul.value == '10') {
    /*on a mis la valeur en str donc il faut aussi la mettre en str ici */
    score += 1
  }
  if (Eiffel.value == 'Paris') {
    score += 1
  }

  alert(`Votre score est de ${score} sur 3`)
}
function reset(event: Event): void {
  event.preventDefault()

  cheval.value = null
  calcul.value = null
  Eiffel.value = null
}
</script>

<template>
  <form>
    <QuestionRadio
      id="cheval"
      v-model="cheval"
      text="De quelle couleur est le cheval blanc de Napoléon ?"
      :options="[
        { value: 'blanc', text: 'Blanc' },
        { value: 'brun', text: 'Brun' },
        { value: 'noir', text: 'Noir' },
      ]"
    />
    <!--ça importe ce qu'il y a dans le questiontext-->
    <QuestionText
      id="exampleFormControlInput"
      v-model="model"
      text="De quelle couleur est le cheval blanc de Napoléon ?"
      placeholder="Veuillez saisir une couleur"
    />

    <QuestionRadio
      id="calcul"
      v-model="calcul"
      text=" Combien font 2+3+5 ?"
      :options="[
        { value: '10', text: '10' },
        { value: '9', text: '9' },
        { value: '12', text: '12' },
      ]"
    />

    <QuestionRadio
      id="Eiffel"
      v-model="Eiffel"
      text=" Où se trouve la Tour-Eiffel ?"
      :options="[
        { value: 'Oslo', text: 'Oslo' },
        { value: 'Sydney', text: 'Sydney' },
        { value: 'Paris', text: 'Paris' },
      ]"
    />

    <button class="btn btn-primary" :class="{ disabled: !filled }" @click="submit">Terminer</button>
    <button class="btn btn-primary" @click="reset">Réinitialiser</button>
  </form>

  <!-- Ancien code HTML qui prend bien plus de place
    De quelle couleur est le cheval blanc de Napoléon ?
    <div class="form-check">
      <input
        id="chevalBlanc"
        v-model="cheval"
        class="form-check-input"
        type="radio"
        name="cheval"
        value="blanc"
      />
      <label class="form-check-label" for="chevalBlanc">Blanc</label>
    </div>
    <div class="form-check">
      <input
        id="chevalBrun"
        v-model="cheval"
        class="form-check-input"
        type="radio"
        name="cheval"
        value="brun"
      />
      <label class="form-check-label" for="chevalBrun">Brun</label>
    </div>
    <div class="form-check">
      <input
        id="chevalNoir"
        v-model="cheval"
        class="form-check-input"
        type="radio"
        name="cheval"
        value="noir"
      />
      <label class="form-check-label" for="chevalNoir">Noir</label>
    </div>

    partie 2 pour la 2ème question

    COmbien font 2+3+5 ?
    <div class="form-check">
      <input
        id="calcul1"
        v-model="calcul"
        class="form-check-input"
        type="radio"
        name="calcul"
        value="10"
      />
      <label class="form-check-label" for="calcul1">10</label>
    </div>
    <div class="form-check">
      <input
        id="calcul2"
        v-model="calcul"
        class="form-check-input"
        type="radio"
        name="calcul"
        value="12"
      />
      <label class="form-check-label" for="calcul2">12</label>
    </div>
    <div class="form-check">
      <input
        id="calcul3"
        v-model="calcul"
        class="form-check-input"
        type="radio"
        name="calcul"
        value="15"
      />
      <label class="form-check-label" for="calcul3">15</label>
    </div>
    <div class="form-check">
      <input
        id="calcul4"
        v-model="calcul"
        class="form-check-input"
        type="radio"
        name="calcul"
        value="9"
      />
      <label class="form-check-label" for="calcul4">9</label>
    </div>

    partie 3 pour la 3ème question
    Où se trouve la Tour-Eiffel ?
    <div class="form-check">
      <input
        id="Eiffel1"
        v-model="Eiffel"
        class="form-check-input"
        type="radio"
        name="Sydney"
        value="Sydney"
      />
      <label class="form-check-label" for="Eiffel1">Sydney</label>
    </div>
    <div class="form-check">
      <input
        id="Eiffel2"
        v-model="Eiffel"
        class="form-check-input"
        type="radio"
        name="Oslo"
        value="Oslo"
      />
      <label class="form-check-label" for="Eiffel2">Oslo</label>
    </div>
    <div class="form-check">
      <input
        id="Eiffel3"
        v-model="Eiffel"
        class="form-check-input"
        type="radio"
        name="Paris"
        value="Paris"
      />
      <label class="form-check-label" for="Eiffel3">Paris</label>
    </div>
    <div class="form-check">
      <input
        id="Eiffel4"
        v-model="Eiffel"
        class="form-check-input"
        type="radio"
        name="Lausanne"
        value="Lausanne"
      />
      <label class="form-check-label" for="Eiffel4">Lausanne</label>
    </div>
          LES BOUTONS DOIVENT ÊTRE DANS LE FORM POUR BIEN MARCHER-->
</template>
