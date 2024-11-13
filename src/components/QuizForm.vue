<script setup lang="ts">
  import { computed, ref } from "vue";

  
  const cheval = ref<string | null>(null);
  const calcul = ref<string | null>(null);
  const Eiffel = ref<string | null>(null);
  
  const filled = computed<boolean>(() => cheval.value !== null);

  let score = 0 ; /* initialisation du score à 0*/ 
  let bonnereponse = [cheval, 10, Eiffel,] /*liste mixte des bonnes réponses*/

  function submit(event: Event): void {
    if (cheval.value == "blanc") {/*comparaison de l'entrée avec les bonnes réponses. aussi bien faire attention à bien mettre les parenthèses + faire plusieurs conditions pour chaque réponse */ {
      score +=1; /*incrémenter le score pour chaque bonne réponse trouvée*/ 
    }}
   /*Mettre ICI une condition pour incrémenter le score afin que ça fasse plus 1 à chaque bonne réponse. Il faut le faire en Javascript. créer la variable 1score1, */
    event.preventDefault();
    if (filled.value) {
      alert(`Vous avez choisi le score ${score} !`); /*alerte score final*/
    }
    else {
      alert('Vous avez pas réussi à avoir toutes les bonnes réponses')
    }
  } 
  function resetquiz(): any {
    console.log('Le quizz a été réinitialisé')
  }
</script>
<!--Bouton de réinitialisation du quiz-->

<button class="btn btn-secondary" @click="reset">Réinitialiser</button>

<!--Un template pour toutes les questions-->
<template>  <!--partie 1 pour les premières questions-->
  <form @submit="submit">
    De quelle couleur est le cheval blanc de Napoléon ?
    <div class="form-check">
      <input
        id="chevalBlanc"
        v-model="cheval"
        class="form-check-input"
        type="radio"
        name="cheval"
        value="blanc"
      />
      <label class="form-check-label" for="chevalBlanc">Blanc</label>
    </div>
    <div class="form-check">
      <input
        id="chevalBrun"
        v-model="cheval"
        class="form-check-input"
        type="radio"
        name="cheval"
        value="brun"
      />
      <label class="form-check-label" for="chevalBrun">Brun</label>
    </div>
    <div class="form-check">
      <input
        id="chevalNoir"
        v-model="cheval"
        class="form-check-input"
        type="radio"
        name="cheval"
        value="noir"
      />
      <label class="form-check-label" for="chevalNoir">Noir</label>
    </div>
   
  </form>

  <!--partie 2 pour la 2ème question-->
  <form @submit="submit">
    COmbien font 2+3+5 ?
    <div class="form-check">
      <input
        id="calcul1"
        v-model="calcul"
        class="form-check-input"
        type="radio"
        name="calcul"
        value="10"
      />
      <label class="form-check-label" for="calcul1">10</label>
    </div>
    <div class="form-check">
      <input
        id="calcul2"
        v-model="calcul"
        class="form-check-input"
        type="radio"
        name="calcul"
        value="12"
      />
      <label class="form-check-label" for="calcul2">12</label>
    </div>
    <div class="form-check">
      <input
        id="calcul3"
        v-model="calcul"
        class="form-check-input"
        type="radio"
        name="calcul"
        value="15"
      />
      <label class="form-check-label" for="calcul3">15</label>
    </div>
    <div class="form-check">
      <input
        id="calcul4"
        v-model="calcul"
        class="form-check-input"
        type="radio"
        name="calcul"
        value="9"
      />
      <label class="form-check-label" for="calcul4">9</label>
    </div>
  
  </form>


<!--partie 3 pour la 3ème question-->
  <form @submit="submit">
    Où se trouve la Tour-Eiffel ?
    <div class="form-check">
      <input
        id="Eiffel1"
        v-model="Eiffel"
        class="form-check-input"
        type="radio"
        name="Sydney"
        value="Sydney"
      />
      <label class="form-check-label" for="Eiffel1">Sydney</label>
    </div>
    <div class="form-check">
      <input
        id="Eiffel2"
        v-model="Eiffel"
        class="form-check-input"
        type="radio"
        name="Oslo"
        value="Oslo"
      />
      <label class="form-check-label" for="Eiffel2">Oslo</label>
    </div>
    <div class="form-check">
      <input
        id="Eiffel3"
        v-model="Eiffel"
        class="form-check-input"
        type="radio"
        name="Paris"
        value="Paris"
      />
      <label class="form-check-label" for="Eiffel3">Paris</label>
    </div>
    <div class="form-check">
      <input
        id="Eiffel4"
        v-model="Eiffel"
        class="form-check-input"
        type="radio"
        name="Lausanne"
        value="Lausanne"
      />
      <label class="form-check-label" for="Eiffel4">Lausanne</label>
    </div>
    <button
      class="btn btn-primary"
      :class="{ disabled: !filled }"
      type="submit"
    >
      Terminer
    </button>
  </form>

</template>

