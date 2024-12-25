<script setup lang="ts">
import { QuestionState } from '@/utils/models'
import { computed, ref, watch, type PropType } from 'vue'

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
  {{ props.text }}
  <div v-for="option in props.options" :key="option.value" class="form-check">
    <input
      :id="`${props.id}-${option.value}`"
      v-model="value"
      class="form-check-input"
      :disabled="
        model === QuestionState.Submit ||
        model === QuestionState.Correct ||
        model === QuestionState.Wrong
      "
      :name="props.id"
      type="radio"
      :value="option.value"
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
