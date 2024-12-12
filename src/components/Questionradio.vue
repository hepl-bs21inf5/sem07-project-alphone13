<script setup lang="ts">
import { ref, watch, type PropType } from 'vue'
import { defineModel, computed } from 'vue'
import { QuestionState } from '@/utils/models' //définition générale de chaque propriété
const model = defineModel<QuestionState>() //le composant
const props = defineProps({
  //un props est une valeur définie par rapport à un type, c'est une propriété du composant
  id: { type: String, required: true },
  text: { type: String, required: true },
  answer: { type: String, required: true },
  answerDetail: { type: String, default: '' },
  options: {
    type: Array as PropType<Array<{ value: string; text: string }>>,
    required: true,
  },
})

const answerText = computed<string>(
  () => props.options.find((option) => option.value === props.answer)?.text ?? props.answer,
)

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
  <!--Fait appel au question de quizform et remplace les valeur des questions -->
  {{ props.text }}
  <div v-for="option in props.options" :key="option.value" class="form-check">
    <input
      :id="`${props.id}-${option.value}`"
      v-model="value"
      class="form-check-input"
      type="radio"
      :name="props.id"
      :value="option.value"
      :disabled="
        model === QuestionState.Submit ||
        model === QuestionState.Correct ||
        model === QuestionState.Wrong
      "
    />
    <label class="form-check-label" :for="`${props.id}-${option.value}`">
      {{ option.text }}
    </label>
  </div>
  <div v-if="model === QuestionState.Correct || model === QuestionState.Wrong">
    <p v-if="model === QuestionState.Correct" class="text-success">Juste !</p>
    <p v-else class="text-danger">Faux ! La réponse était : {{ answerText }}</p>
    <p class="blockquote-footer">{{ props.answerDetail }}</p>
  </div>
</template>
<style scoped>
.text-danger {
  color: rgb(128, 0, 0) !important;
}
.text-success {
  color: rgb(196, 34, 196) !important;
}
</style>