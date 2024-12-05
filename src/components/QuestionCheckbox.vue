<script lang="ts">
import { ref, watch, type PropType } from 'vue'
import { defineModel, defineProps } from 'vue'
import { QuestionState } from '@/utils/models' //définition générale de chaque propriété

const checkedNames = ref<string[]>([])
const model = defineModel<QuestionState>() //le composant
const props = defineProps({
  //un props est une valeur définie par rapport à un type, c'est une propriété du composant
  id: { type: String, required: true },
  text: { type: String, required: true },
  answer: { type: Array as PropType<String[]>, required: true },
  options: {
    type: Array as PropType<Array<{ value: string; text: string }>>,
    required: true,
  },
})

const value = ref<string | null>(null)

watch(
  //Un watch c'est pour exécuter à chaque fois que la value change et màj de la valeur du modèle
  value,
  (newValue) => {
    if (newValue === null) {
      model.value = QuestionState.Empty //la question de type vide
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
    //Condition en plus pour vérifier si la réponse a été envoyée
    value.value = null
  }
})
</script>

<template>
  <!--Le template est pour la mise en page-->
  <div class="form-check">
    <input
      id="checkboxJane"
      v-model="checkedNames"
      class="form-check-input"
      type="checkbox"
      value="Jane"
    />
    <label class="form-check-label" for="checkboxJane">Jane</label>
  </div>
  <div class="form-check">
    <input
      id="checkboxJohn"
      v-model="checkedNames"
      class="form-check-input"
      type="checkbox"
      value="John"
    />
    <label class="form-check-label" for="checkboxJohn">John</label>
  </div>
</template>
