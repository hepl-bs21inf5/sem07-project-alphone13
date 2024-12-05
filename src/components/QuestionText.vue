<script setup lang="ts">
import { defineModel } from 'vue'
import { ref, watch } from 'vue'
import { QuestionState } from '@/utils/models'

//const model = defineModel<string | null>(), on enlève car on le prend depuis le questionsate
//composant similaire à Radio.
//const model = defineModel<boolean>(), ce n'est plus un booléen on doit le mettre sous forme de question state

const model = defineModel<QuestionState>()
const props = defineProps({
  id: { type: String, required: true },
  text: { type: String, required: true },
  answer: { type: String, required: true },
  placeholder: { type: String, default: 'Veuillez saisir une réponse' },
})

const value = ref<string | null>(null)

watch(
  value,
  (newValue) => {
    if (newValue === null) {
      model.value = QuestionState.Empty
    } else {
      model.value = QuestionState.Fill
    }
  },
  { immediate: true },
)

watch(model, (newModel) => {
  if (newModel === QuestionState.Submit) {
    model.value = value.value === props.answer ? QuestionState.Correct : QuestionState.Wrong
  } else if (newModel === QuestionState.Empty) {
    value.value = null
  }
})
</script>

<template>
  <label for="exampleFormControlInput" class="form-label">
    Quel est le meilleur anime de tous les temps ?
  </label>
  <input
    id="exampleFormControlInput"
    v-model="value"
    class="form-control"
    placeholder="Saisir une réponse"
    :disabled="
      model === QuestionState.Submit ||
      model === QuestionState.Correct ||
      model === QuestionState.Wrong
    "
  />

  <!--là on doit faire comme dans Question radio pour faire ce document
  Le placeholder permet de faire apparaître du texte dans le champ de saisie 
  là on fait un composant pour tous les types de questions-->
</template>
