<!-- A presque les même propriétés que QuestionRadio.vue -->
<script setup lang="ts">
import { ref, watch, defineModel, defineProps, type PropType } from 'vue'
import { QuestionState } from '@/utils/models'

const model = defineModel<QuestionState>()

//même que dans QuestionRadio.vue
const props = defineProps({
  id: { type: String, required: true },
  text: { type: String, required: true },
  answerDetail: { type: String, default: '' },
  answer: { type: Array as PropType<string[]>, required: true }, // on doit initier afin que la réponse est une liste
  options: {
    type: Array as PropType<Array<{ value: string; text: string }>>,
    required: true,
  },
})
const value = ref<string[]>([])

watch(
  value,
  (newValues) => {
    if (newValues.length === 0) {
      model.value = QuestionState.Empty
    } else if (model.value !== QuestionState.Submit) {
      model.value = QuestionState.Fill
    }
  },
  { immediate: true },
)

watch(model, (newModel) => {
  if (newModel === QuestionState.Submit) {
    const isCorrect =
      props.answer.length === value.value.length &&
      props.answer.every((val) => value.value.includes(val))
    model.value = isCorrect ? QuestionState.Correct : QuestionState.Wrong
  } else if (newModel === QuestionState.Empty) {
    value.value = []
  }
})
</script>

<template>
  <p>{{ props.text }}</p>
  <div v-for="option in props.options" :key="option.value" class="form-check">
    <input
      :id="`${props.id}-${option.value}`"
      v-model="value"
      class="form-check-input"
      type="checkbox"
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
    <p v-else class="text-danger">Faux ! Les réponses étaient : {{ props.answer.join(', ') }}</p>
    <p v-if="props.answerDetail" class="blockquote-footer">{{ props.answerDetail }}</p>
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
