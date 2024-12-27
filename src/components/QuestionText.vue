<script setup lang="ts">
import { defineModel, type PropType } from 'vue'
import { ref, watch } from 'vue'
import { QuestionState } from '@/utils/models'

const model = defineModel<QuestionState>()
const props = defineProps({
  id: { type: String, required: true },
  text: { type: String, required: true },
  answer: { type: Array as PropType<Array<string>>, required: true },
  answerDetail: { type: String, default: '' },
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
    model.value = props.answer.includes(value.value ?? '')
      ? QuestionState.Correct
      : QuestionState.Wrong
  } else if (newModel === QuestionState.Empty) {
    value.value = null
  }
})
</script>
<template>
  <label for="exampleFormControlInput" class="form-label"> Combien de pattes a un chat ? </label>
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
  <div v-if="model === QuestionState.Correct || model === QuestionState.Wrong">
    <p v-if="model === QuestionState.Correct" class="text-success">Juste !</p>
    <p v-else class="text-danger">Faux ! La réponse était : {{ props.answer }}</p>
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
