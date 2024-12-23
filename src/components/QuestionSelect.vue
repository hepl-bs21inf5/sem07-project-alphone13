<script setup lang="ts">
import { ref, computed, watch, defineProps, type PropType } from 'vue'
import { QuestionState } from '@/utils/models'

// Définir les props pour ce composant
const props = defineProps({
  id: { type: String, required: true },
  text: { type: String, required: true },
  answer: { type: String, required: true },
  options: {
    type: Array as PropType<Array<{ value: string; text: string }>>,
    required: true,
  },
  answerDetail: { type: String, default: '' },
})

// État local
const selectedValue = ref<string | null>(null) // La valeur sélectionnée
const model = ref<QuestionState>(QuestionState.Empty) // L'état de la question

// Calcul pour obtenir le texte de la réponse correcte
const correctAnswerText = computed<string>(
  () => props.options.find((option) => option.value === props.answer)?.text ?? props.answer,
)

// Watch pour mettre à jour l'état selon la sélection
watch(selectedValue, (newValue) => {
  if (newValue === null) {
    model.value = QuestionState.Empty
  } else {
    model.value = QuestionState.Fill
  }
})

// Watch pour vérifier si la question est soumise
watch(model, (newModel) => {
  if (newModel === QuestionState.Submit) {
    model.value = selectedValue.value === props.answer ? QuestionState.Correct : QuestionState.Wrong
  } else if (newModel === QuestionState.Empty) {
    selectedValue.value = null
  }
})
</script>

<template>
  <div>
    <p>{{ props.text }}</p>
    <!-- Liste déroulante -->
    <select
      class="form-select"
      :id="props.id"
      v-model="selectedValue"
      :disabled="
        model === QuestionState.Submit ||
        model === QuestionState.Correct ||
        model === QuestionState.Wrong
      "
    >
      <!-- Option par défaut : "Sélectionner une réponse" -->
      <option value="" disabled selected>Sélectionner une réponse</option>
      <option v-for="option in props.options" :key="option.value" :value="option.value">
        {{ option.text }}
      </option>
    </select>

    <!-- Afficher le résultat après soumission -->
    <div v-if="model === QuestionState.Correct || model === QuestionState.Wrong">
      <p v-if="model === QuestionState.Correct" class="text-success">Bonne réponse !</p>
      <p v-else class="text-danger">
        Mauvaise réponse. La réponse correcte est : {{ correctAnswerText }}
      </p>
      <p class="blockquote-footer">{{ props.answerDetail }}</p>
    </div>
  </div>
</template>

<style scoped>
.text-danger {
  color: rgb(128, 0, 0) !important;
}
.text-success {
  color: rgb(34, 139, 34) !important;
}
</style>
