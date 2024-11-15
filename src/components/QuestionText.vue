<script setup lang="ts">
import { defineModel } from 'vue'
const model = defineModel<string | null>()
</script>

<template>
  <label for="exampleFormControlInput" class="form-label">
    Quel est le meilleur anime de tous les temps ?
  </label>
  <input
    id="exampleFormControlInput"
    v-model="model"
    class="form-control"
    placeholder="Saisir une réponse"
  />
  <!--là on doit faire comme dans Question radio pour faire ce document
  Le placeholder permet de faire apparaître du texte dans le champ de saisie -->
</template>
