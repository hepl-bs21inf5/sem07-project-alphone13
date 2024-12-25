<script setup lang="ts">
import { QuestionState } from '@/utils/models'
import { computed, ref, watch, type PropType } from 'vue'
//inspiré de QuestionRadio
const model = defineModel<QuestionState>()
const props = defineProps({
  id: { type: String, required: true },
  text: { type: String, required: true },
  answer: { type: String, required: true },
  answerDetail: { type: String, default: '' },
  options: {
    type: Array as PropType<Array<{ value: string; text: string }>>,
    required: true,
  },
})

const value = ref<string | null>(null)
const answerText = computed<string>(
  () => props.options.find((option) => option.value === props.answer)?.text ?? props.answer,
)

// Watchers pour mettre à jour l'état de la question selon la sélection
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

// Mettre à jour l'état de la question lors de la soumission
watch(model, (newModel) => {
  if (newModel === QuestionState.Submit) {
    model.value = value.value === props.answer ? QuestionState.Correct : QuestionState.Wrong
  } else if (newModel === QuestionState.Empty) {
    value.value = null
  }
})
</script>

<template>
  <div>
    <!-- Affichage de la question -->
    <label :for="props.id">{{ props.text }}</label>

    <!-- Menu déroulant (select) -->
    <select
      :id="props.id"
      v-model="value"
      :disabled="model === QuestionState.Submit || model === QuestionState.Correct || model === QuestionState.Wrong"
      class="form-select"
    >
      <option value="" disabled selected>Sélectionnez une réponse</option>
      <option
        v-for="option in props.options"
        :key="option.value"
        :value="option.value"
      >
        {{ option.text }}
      </option>
    </select>

    <!-- Affichage du résultat après soumission -->
    <div v-if="model === QuestionState.Correct || model === QuestionState.Wrong">
      <p v-if="model === QuestionState.Correct" class="text-success">Juste !</p>
      <p v-else class="text-danger">Faux ! La réponse était : {{ answerText }}</p>
      <p class="blockquote-footer">{{ props.answerDetail }}</p>
    </div>
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
