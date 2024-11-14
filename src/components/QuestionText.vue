<script setup lang="ts">
import { defineModel } from 'vue'
const model = defineModel<string | null>()
</script>

<template>
  <label for="exampleFormControlInput" class="form-label">
    Combien de cantons dans la Suisse ?
  </label>
  <input
    id="exampleFormControlInput"
    v-model="model"
    class="form-control"
    placeholder="Veuillez saisir une couleur"
  />
  <!--là on doit faire comme dans Question radio pour faire ce document-->
</template>
