# JOURNAL DE BORD

## Réponses aux questions avec mes propres mots

un watch est un handler. Il observe une donnée et quand la donnée change le watch s'exécute.

Un handler (ou gestionnaire en français) est une fonction ou un bloc de code que vous définissez pour répondre à un événement ou à une situation particulière (pris de Chat)

Proposer une autre manière de calculer le score et comparer les deux méthodes.

# Temps

commencé à 10h15 et finis ce que qu'il fallait faire vers environ 11h30

## Améliorations des composants

#### Problèmes rencontrés avec les boutons terminer et réinitialiser

J'arrivais pas à faire fonctionner les boutons correctement. J'ai dû demander de l'aide car je ne trouvais pas l'erreur. En fait, les boutons marchaient correctement que après avoir cliquer sur 'réinitialiser'. Puis par la suite c'était le bouton réinitialiser qui ne marchait pas. Je suis restée bloquer dessus pendant un bon moment et j'ai demandé de l'aide au prof.

Ce dont j'ai compris avec ça c'est qu'il faut bien faire attention à bien lier les valeurs avec leurs propriétés. Aussi il faut faire attention à la manière dont on définit les constantes et les imports car sinon le code ne marche pas. Finalement, j'ai décidé de tout effacer et de recommencer afin de voir si le problème venait des imports ou bien des fonctions. J'ai vu que le problème venait de la synchronisation et de la gestion associées aux boutons.

La gestion des états des boutons était compliquée dans le premier code car les bouton n'appelaient pas de méthodes bien définies. En fait, la gestion des boutons se fait avec questionState. Et dans le premier code j'ai mal lié les états de questionState et c'est pour ça qu'il y avait des incohérences.

J'ai ensuite déclaré les constantes (états des question, score, total score, rempli, et envoyé) et c'était similaire à quizForm. Pour j'ai défini les différentes actions (méthodes) qui vont envoyer les résultats, réinitiliser les questions cochées, mélanger les questions (fetchQuestions) et qui mélange les réponses.

#### QuestionSelect.Vue

J'ai implémenté une question avec une sélection multiple dans **QuizForm.Vue**:

et j'ai également mis dans **QuizForm.Vue** une question type déroulant.
Pour que la logique du code puisse toujours marcher, j'ai transformé certaines parties.

const questionStates = ref<QuestionState[]>([])

en
const questionStates = ref<QuestionState[]>(new Array(questions.value.length).fill(QuestionState.Empty));

1. **Validation et retour utilisateur** :
   - Ajouter des boutons de validation et de réinitialisation des réponses.
   - Améliorer le feedback utilisateur avec des messages clairs et des animations.
2. **Gestion des réponses incorrectes** :
   - Intégrer une indication visuelle pour signaler les réponses incorrectes.
3. **Optimisation de l'interface utilisateur** :
   - Rendre le design plus interactif et accessible avec des composants Vue et Bootstrap.
4. **Gestion avancée des scores** :

   - Enregistrer les scores pour permettre une analyse à long terme.

   1. **Personnalisation et feedback utilisateur** :

   - Ajouter des messages ou animations pour indiquer les réponses correctes ou incorrectes.
   - Améliorer la gestion des erreurs pour guider l’utilisateur.

5. **Optimisation des interactions** :

   - Intégrer une barre de progression pour visualiser l’avancement.
   - Simplifier les transitions pour les rendre plus intuitives.

```JS

```

```JS

```

# Rapport de Projet - Semaine 1

## Temps de travail

- **Temps estimé** : 30 minutes
- **Temps passé** : ~45 minutes

## Tâches réalisées

Pour cette première semaine, j'ai accompli plusieurs étapes importantes pour bien avancer sur le projet. Voici comment cela s'est passé :

D'abord, j'ai cloné le dépôt Git sur mon ordinateur et configuré l'environnement de travail. Ensuite, j'ai installé l'extension Vue - Official dans Visual Studio Code, qui est très utile pour travailler avec Vue.js. Après cela, j'ai copié et organisé les fichiers dans le répertoire sem07-project-alphone13, en suivant les consignes pour tout structurer correctement.

J'ai installé toutes les dépendances nécessaires avec npm install, puis j'ai vérifié que le projet se lançait bien en mode développement avec `npm run dev`.

J'ai fait un peu de nettoyage et instalé les composants principaux (comme main.ts, App.vue, etc.). Cela m'a permis de mieux organiser le projet.

La partie la plus intéressante était de créer le quiz. J'ai ajouté des questions à choix multiples, calculé le score, et inclus des fonctionnalités sympas comme par exempleun message de félicitations si le score est parfait.

Enfin, j'ai changé quelques styles pour personnaliser l'application, et j'ai ajouté des icônes Bootstrap dans la barre de navigation pour un rendu plus moderne.

## Difficultés rencontrées et solutions

### Difficultés

1. **Compréhension des différences entre ref et computed** :
   - Les différences entre ces deux concepts n'étaient pas claires au premiers abords.
2. **Erreur lors de l'installation des dépendances** :
   - la page web ne saffichait pas dans le navigateur et j'ai pris du retard.

### Solutions

1. **Documentation et exemples** :
   - Lecture de la documentation officielle Vue.js et implémentation d'exemples pour comprendre ref et computed.
2. **Configuration corrigée** :
   - Remplacement de l'ancienne configuration par celle demandée par le prof.

## Réponses aux questions

### Rôle des fichiers principaux

1. **main.ts** :
   - Initialise l'application Vue, configure le routeur, et monte l'application dans le DOM (le DOM, qui est une représentation en mémoire de la page web et permet de modifier ou de lire une page web).
     (Il est en TypeScript)
2. **main.css** :
   - Permet de gérer le style de la page HTML en personnalisant l'apparence de l'application (par exemple, la couleur des boutons).
3. **App.vue** :
   - Composant racine de l'application qui contient la structure globale (inclus les composants enfants via le routeur).
4. **router/index.ts** :
   - Gère la navigation entre les différentes pages de l'application.
5. **AboutView.vue** et **HomeView.vue** :
   - Composants Vue représentant respectivement les pages À propos et Accueil.
     Aboutview.vue: Affiche le texte de l'index 'À propos'
     HomeView.vue : document HTML contenant le titre et affiche le titre
6. **QuizForm.vue** :
   - Composant principal pour le quiz, contenant la logique et les éléments interactifs du formulaire. Permet de créer la page de quiz avec les question et réponses en HTML et Javascript

### Quelles sont les similarités et les différences entre ref et computed ?

- **ref** :
  - est ulisisé pour les valeurs réactives. Les valeurs qu'il retourne ont une propriété '.value' et si la valeur est un objet vue.js, il le met automatiquement à jour.
  - Utilisé pour stocker des états dynamiques ou des données modifiables.
- **computed** :
  - C'est une fonction qui permet de calculer une valeur en fonction des données existantes. Il met aussi à jour les valeurs en cas de modifications. (valeur dérivée)

ref et computed sont tous les deux réactifs, donc ils mettent à jour l’écran quand leur valeur change.La diférence entre le ref et computed réside dans les valeurs. Si une valeur peut être directement modifiée alors on utilise le ref et computed alcule une valeur à partir d’autres données.

#### Que se passe-t-il lorsqu'on clique sur le bouton "Terminer" ?

Il permet de terminer le quiz et d'envoyer les réponses afin de vérifier si elles sont justes. Lorsque l'utilisateur clique sur "Terminer", la fonction `submit` est appelée. Elle empêche l'action par défaut (event.preventDefault), calcule le score, et affiche le résultat.

#### Qu'est-ce qu'un v-model ?

C'est une commande qui permet de lier une donnée JavaScript et un élément HTML automatiquement. Par exemple, si il y a un chamgement de valeur dans le code HTML, il y a une mise à jour automatique dans le JavaScript. (Liaison bidirectionnelle)

#### À quoi sert le :class="{ disabled: !filled }" ?

Ajoute dynamiquement une classe CSS à un élément si la condition (!filled) est vraie. Ici, "disabled" est appliqué pour griser un bouton tant que toutes les réponses ne sont pas remplies.
Il sert à lier l'attribut 'class' d'un élément HTML avec un élément du JavaScript et rend la class dynamique.

# Rapport de Projet - Semaine 2

## Temps de travail

- **Temps estimé** : 30 minutes
- **Temps passé** : 45 minutes

## Tâches réalisées

Durant cette semaine, plusieurs étapes importantes ont été franchies pour enrichir le projet et le rendre plus fonctionnel :

1. **Création d'un composant QuestionRadio** :
   J'ai d'abord développer d'un composant `QuestionRadio.vue` pour gérer les questions à choix multiples et éviter la répétition de code dans `QuizForm.vue`. Ce composant permet de recevoir et gérer dynamiquement les données des questions et options via des propriétés.

Ensuite j'ai travaillé sur la conception d'un composant `QuestionText.vue` pour les questions nécessitant des réponses libres. Ce composant accepte des propriétés comme `v-model`, `id`, `text` et un `placeholder`.

Puis on a ajouté une fonctionnalités pour récupérer des questions de quiz dynamiques via l'API [Open Trivia Database](https://opentdb.com/api.php?amount=10&type=multiple). Et implémentation de code dans le composants `QuizTrivia.vue`. On a ensuite procédé à la mise en place d'une nouvelle vue `TriviaView.vue` accessible depuis la barre de navigation et à son ajout dans le fichier `router/index.ts`.
Puis finalement, on a un peu travaillé avec un composant `QuestionCheckbox.vue` pour gérer les questions permettant plusieurs réponses. Mais je ne l'ai fini qu'à la semaine 6.

## Difficultés rencontrées et solutions

### Difficultés

1. **Manipulation des propriétés dynamiques** :
   - Intégration des propriétés `defineProps` et `defineModel` dans les composants Vue.
2. **Décodage des données de l'API Trivia** :
   - Les entités HTML dans les questions rendaient leur lecture difficile.

### Solutions

**Tests progressifs** :
je me suis aidé de npm run dev et npm run build pour voir si mon code marchait, mais à ce moment-là je ne comprenais pas encore ce que m'affichait le terminal.

## Réponses aux questions

### Quelle est la différence entre un prop et un modèle (v-model) ?

- **Prop** :

  - Permet de transmettre des données d'un parent à un enfant.
  - Non-modifiable dans le composant enfant.

- **v-model** :

  - Assure une liaison bidirectionnelle entre le parent et l'enfant.
  - Permet à l'enfant de modifier les données reçues.

  Un **prop**, c'est comme passer une information à un composant enfant pour qu'il l'utilise, mais sans qu'il puisse la modifier (non muable). En revanche, un **v-model** permet de partager une donnée entre le parent et l'enfant, où chacun peut la mettre à jour, et les deux voient les changements en même temps.

### Comment rendre la propriété placeholder optionnelle ?

- Exemple avec `placeholder` dans `QuestionText.vue` :
  ```ts
  placeholder: { type: String, default: "" }
  ```

### Fonctionnement de Trivia

- **Composant TriviaView.vue** :
  Le composant Trivia récupère des questions dynamiques depuis l'API à la création du composant et utilise `QuestionRadio` pour afficher les options de réponses.

# Journal de Bord - Semaine 3

## Temps de travail

- **Temps estimé** : 30 minutes
- **Temps passé** : 45 minutes

## Tâches réalisées

Cette semaine, les efforts ont été concentrés sur l’amélioration des composants et du calcul des scores dans le projet. Voici les tâches principales :

Premièrement, on a intégré une logique permettant de vérifier si la réponse de l’utilisateur est correcte directement dans chaque composant de question. Puis on a mis en place de la propriété `answer` dans `QuestionRadio.vue` et `QuestionText.vue` pour stocker la réponse correcte. Ensuite, on a implémenté la fonction `watch` pour comparer la réponse de l'utilisateur avec la réponse correcte et mettre à jour dynamiquement un modèle réactif.

On a par la suite crée une version plus compacte du code. C'est bien plus long en matière de code.
Voici l'ancienne version du code :

```HTML
  <!-- Ancien code HTML qui prend bien plus de place dans le composant-->
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

    <!--partie 2 pour la 2ème question-->

    Combien font 2+3+5 ?
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

    <!--partie 3 pour la 3ème question-->
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
```

Deuxièmement, on a travaillé sur la gestion des réponses correctes avec l'introduction de `correctAnswers` dans `QuizForm.vue` et sur la modification des composants pour lier `v-model` à `correctAnswers`, facilitant ainsi le suivi des réponses correctes. on a mis en place une propriété qui calcule (`computed`) afin d'évaluer le score total basé sur les réponses correctes et on a ajouté l'affichage du score dans `QuizForm.vue`. Finalement, on a procédé à la suppression de l’ancienne logique de calcul du score, remplacée par une méthode plus efficace, puis à un nettoyage général du code pour améliorer la lisibilité et réduire la complexité.

## Réponses aux questions

**À quoi sert l'option immediate: true dans le watch ?**
à executer la fonction de rappel watch et à synchroniser les données dès le départ. Il est utilisé pour la réactivité des changements de valeur. Il faut que le watch soit configuré pour que immediate : true marche.

**Que se passe-t-il si on l'enlève ou si on met immediate: false ?**
Si on enlève immediate: true, la fonction dans le watch ne se lancera pas tout de suite. Elle attendra que la valeur qu'on observe change pour la première fois.

Donc, avec immediate: true, la mise à jour se fait dès le départ, sans immediate: true, elle se fait seulement après un changement.

**Proposer une autre manière de calculer le score et comparer les deux méthodes.**
On a modifié le code pour le calcul du score. Voici l'ancien code avec les commentaires que j'ai mis pour comprendre comment fonctionne le code:

```JS
function submit(event: Event): void {
  event.preventDefault()
  let score: number = 0
  if (cheval.value === 'blanc') {
    score += 1
  }
     if (cheval.value == "blanc") {/*comparaison de l'entrée avec les bonnes réponses. aussi bien faire attention à bien mettre les parenthèses + faire plusieurs conditions pour chaque réponse */ {
      score +=1; /*incrémenter le score pour chaque bonne réponse trouvée*/
    }}
    if (calcul.value == "10") { {/*on a mis la valeur en str donc il faut aussi la mettre en str ici */
      score +=1;
    }}
    if (Eiffel.value == "Paris") {{
      score +=1;
    }}

    event.preventDefault();
    if (filled.value) {
      alert(`Vous avez choisi le score ${score} !`); /*alerte score final*/
    }
    else {
      alert('Vous avez pas réussi à avoir toutes les bonnes réponses')
    }
  }
  function resetquiz(): any
    console.log('Le quizz a été réinitialisé')
  if (calcul.value == '10') {
    /*on a mis la valeur en str donc il faut aussi la mettre en str ici */
    score += 1
  }
  if (Eiffel.value == 'Paris') {
    score += 1
  }
```

Avant le calcul du score ce faisait dans les fonctions submit et reset.

Explication de l'ancienne méthode :
Le score est initilisé à 0. Pour chaque réponse (cheval, calcul, eiffel), on compare la valeur donnée avec la bonne réponse. Si elles correspondent, le score est incrémenté de 1.
À la fin, le score total s'affiche avec un message clair indiquant le nombre de bonnes réponses.

Autre méthode:

```JS
function submit(event: Event): void {
  event.preventDefault();
  const correctAnswers = [
    { value: cheval.value, correctAnswer: 'blanc' },
    { value: calcul.value, correctAnswer: '10' },
    { value: Eiffel.value, correctAnswer: 'Paris' }
  ];

  let score: number = 0;

  // Comparer chaque réponse avec la bonne réponse
  correctAnswers.forEach(answer => {
    if (answer.value === answer.correctAnswer) {
      score += 1; // Si la réponse est correcte, incrémenter le score
    }
  });

  // Affichage du score final
  if (filled.value) {
    alert(`Vous avez choisi le score ${score} !`);
  } else {
    alert('Vous n\'avez pas réussi à avoir toutes les bonnes réponses');
  }
}

// Fonction de réinitialisation du quiz
function resetquiz(): any {
  console.log('Le quizz a été réinitialisé');
  score = 0; // réinitialisation du score
}
```

Explication de la proposition de code:
Un tableau (définit par des []) correctAnswers est utilisé pour stocker les réponses de l'utilisateur (value) et les bonnes réponses (correctAnswer).
Boucle forEach : On parcourt chaque objet du tableau et on compare value avec correctAnswer.
Incrémentation : Si les deux valeurs sont égales, le score est incrémenté de 1.
Réinitialisation : Le score est réinitialisé dans la fonction resetquiz.

**Comparaison des deux méthodes**

Ancienne méthode :
Avantages :
Le code est plus flexible et plus facile à maintenir : on peut facilement ajouter de nouvelles réponses sans avoir à ajouter de nouvelles conditions.
La logique est plus concise et plus propre, surtout si on doit gérer plusieurs réponses.

Inconvénients:
Cette version contient des conditions qui vérifient si la réponse est juste et additionne le score sous forme de condition. Le problème est que si nous avons par exemple un quiz à 100 questions, il faudrait faire une conditions pour chacum^ne de ces questions, ce qui rendrait le code beaucoup trop long.

Proposition de code:
Avantages :
Le code est plus flexible et plus facile à maintenir : vous pouvez facilement ajouter de nouvelles réponses sans avoir à ajouter de nouvelles conditions.
La logique est plus concise et plus propre, surtout si vous devez gérer plusieurs réponses.

Inconvénients :
Le tableau peut rendre la logique plus abstraite, bien qu'elle soit plus propre.
Moins explicite pour un débutant si le nombre de réponses est faible.

## Difficultés rencontrées et solutions

Cette fois-ci j'ai cru que j'allais passé plus de temps, car je ne comprenais pas au début ce qui était demandé. Mais en demandant de l'aide j'ai pu surpasser cette difficulté.

### Difficultés

1. **Compréhension du comportement de `watch`** :
   - Nécessité d'utiliser l'option `immediate: true` pour assurer une synchronisation initiale des valeurs.
2. **Mise à jour réactive des scores** :
   - Gérer correctement les données réactives et leur comportement dans les composants.

### Solutions

1. **Tests approfondis** :
   J'ai dû observer les comportements dans différents scénarios pour comprendre l’impact des modifications. J'ai fait de la recherche sur les `computed` et `watch` pour mieux appréhender leur fonctionnement à l'aide de ChatGPT.

## Explications et réflexions sur le code

### Utilisation de `immediate: true` dans `watch`

- **Avec `immediate: true`** : La fonction de `watch` s'exécute dès que le composant est monté.
- **Sans cette option** : La fonction de `watch` ne s'exécute qu'à la première modification de la valeur suivie.

### Calcul du score

- Méthode utilisée :
  - Filtrer les valeurs `true` dans `correctAnswers` pour compter le nombre de réponses correctes.
  - Utilisation de la méthode `filter` et de `length` pour simplifier cette logique.

# Rapport de Projet - Semaine 4

## Temps de travail

- **Temps estimé** : 1 heure
- **Temps passé** : 1 heure 15 minutes

## Tâches réalisées

Cette semaine, l'accent a été mis sur la gestion des états des questions et l'amélioration des interactions utilisateur. Voici un résumé des principales réalisations :

1. **Ajout d'un modèle pour les états des questions** :

   - Création d’un enum `QuestionState` dans un fichier dédié (`src/utils/models.ts`) pour gérer les états possibles : `Empty`, `Fill`, `Submit`, `Correct`, et `Wrong`:

```JS
   export enum QuestionState {
  Empty = "Empty",
  Fill = "Fill",
  Submit = "Submit",
  Correct = "Correct",
  Wrong = "Wrong",
}
```

- Modification des composants pour utiliser ce nouveau modèle au lieu d'un simple booléen pour le suivi des états. Implémentation dans Questionradio:

```JS
import { QuestionState } from '@/utils/models'
...
const model = defineModel<QuestionState>()
...
```

2. **Gestion des transitions d'état** :

   - Mise à jour des composants `QuestionRadio.vue` et `QuestionText.vue` pour gérer les transitions d'état automatiquement via `watch`.
   - Exemple de transitions :
     - Si une réponse est soumise (`Submit`), l’état devient `Correct` ou `Wrong` en fonction de la réponse de l’utilisateur.
     - Si une réponse est annulée (`Empty`), la valeur saisie redevient `null`.

3. **Refonte du stockage des états dans le formulaire** :

   - Introduction de la liste réactive `questionStates` dans `QuizForm.vue` pour suivre l’état de chaque question.
   - Mise à jour du calcul du score en comptant uniquement les questions dans l’état `Correct`.

4. **Gestion des boutons** :

   - **Bouton Terminer** :
     - Soumet toutes les questions en modifiant les états de `questionStates` à `Submit`.
   - **Bouton Réinitialiser** :
     - Réinitialise tous les états à `Empty` et efface les réponses des utilisateurs.

5. **Rendre les réponses non modifiable après soumission** :

   - Désactivation des champs d’entrée si l’état est `Submit`, `Correct`, ou `Wrong`.

6. **Améliorations visuelles et debug** :
   - Ajout d'une div de débogage pour afficher l’état actuel de chaque question.
   - Affichage du score uniquement si toutes les questions ont été envoyées et corrigées.

## Réponses aux questions

Comment pourrait-on réécrire la ligne suivante:

```JS
model.value =
value.value === props.answer ? QuestionState.Correct : QuestionState.Wrong;
```

Sans l'opérateur ternaire (avec des if et else) ?

On peut la réecrire avec des if et else comme ça :

```JS
if (value.value === props.answer) {
model.value = QuestionState.Correct;
} else {
model.value = QuestionState.Wrong;
}
```

Comment pourrait-on réécrire autrement la logique du watch sur value ?

```JS
...
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
);
...
```

On peut la réecrire avec les opérateurs if et else:

```JS
watch(
  value,
  (newValue) => {
    if (newValue === null) {
      model.value = QuestionState.Empty;
    } else {
      model.value = QuestionState.Fill;
    }
  },
  { immediate: true },
);
```

## Difficultés rencontrées et solutions

### Difficultés

Voici une liste des difficultés que j'ai rencontrées:

- S'assurer que tous les champs et états retournent à leur état initial (dons vide) lors d'un reset.
- Vérifier que les boutons intéragissent correctement entre eux.

### Solutions

**Tests rigoureux** :

- Mise en place de scénarios pour valider le comportement attendu de chaque transition d'état.

## Explications et réflexions sur le code

### Gestion des états avec `watch`

- Les `watch` permettent de surveiller les changements dans les réponses et les états pour déclencher des actions :
  - Exemple : Si `value` devient `null`, l’état est mis à jour en `Empty`.
  - Exemple : Si l’état devient `Submit`, le système vérifie la réponse et met à jour l’état en `Correct` ou `Wrong`.

### Calcul du score

On a changé la forme des méthodes function submit et reset dans QuizForm.Vue. Voici l'ancienne version:

```JS
function submit(event: Event): void {
event.preventDefault()
let score: number = 0
if (cheval.value === 'blanc') {
score += 1
}

if (calcul.value == '10') {
score += 1
}
if (eiffel.value == 'Paris') {
score += 1
}

alert(`Votre score est de ${score} sur 3`)
}

function reset(event: Event): void {
event.preventDefault()
cheval.value = null
calcul.value = null
eiffel.value = null
}
```

Cette version contient des conditions qui vérifient si la réponse est juste et additionne le score sous forme de condition. Le problème est que si nous avons par exemple un quiz à 100 questions, il faudrait faire une conditions pour chacum^ne de ces questions, ce qui rendrait le code beaucoup trop long. Nous avons fait une version plus compacte avec `questionStates`.

- Nouvelle méthode :
  - Filtrer les états égaux à `Correct` dans `questionStates` et compter ces valeurs pour obtenir le score.
- Affichage conditionnel :
  - Le score n’est visible que lorsque toutes les réponses sont corrigées (`Correct` ou `Wrong`).

Voici la nouvelle version de submit et rest du QuizForm.Vue:

```JS
// fait des comparaison valeur vide-pleine
function submit(event: Event): void {
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Submit)
   //envoie les réponses rentrées par l'utilisateur
}

function reset(event: Event): void {
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Empty)
  //on met l'état des réponses à vide.
}
```

La nouvelle verison est plus dynamique et plus compacte. Elle contient également les liens entre les différents composants.

# Journal de Bord - Semaine 5

## Temps estimé et temps passé

- **Temps estimé :** 1 heure
- **Temps passé :** 2 heures

## Tâches réalisées

1. **Ajout de la propriété `answerDetail` dans `QuestionText.vue`** :
   - J'ai ajouté une nouvelle propriété `answerDetail` pour afficher des détails supplémentaires lorsque la réponse est correcte ou incorrecte.
2. **Modification du template dans `QuestionText.vue`** :
   - J'ai utilisé `v-if` et `v-else` pour conditionner l'affichage du texte, en indiquant si la réponse était correcte ou fausse, et en ajoutant un champ pour afficher les détails de la réponse.
3. **Mise à jour de `QuizForm.vue`** :
   - J'ai intégré la propriété `answerDetail` dans l'appel du composant `QuestionText` pour permettre l'affichage des détails.
4. **Adaptation de `QuestionRadio.vue`** :
   - J'ai ajouté une computed property `answerText` pour gérer l'affichage des réponses dans `QuestionRadio.vue` et afficher correctement la réponse selon qu'elle provienne d'une option ou d'une valeur brute.
5. **Mise en place des styles personnalisés** :

```JS
<style scoped>
  .text-danger {
    color: purple !important;
  }
</style>
```

- J'ai ajouté du CSS pour changer la couleur des textes de réponse (correctes et incorrectes) et j'ai utilisé `scoped` pour que les styles ne soient appliqués qu'au composant actuel.

## Difficultés rencontrées et solutions trouvées

1. **Problème avec l'affichage des détails (`answerDetail`)** :
   - **Difficulté :** Lorsqu'aucune valeur n'était fournie pour `answerDetail`, rien n'était affiché. Cela a créé un vide qui pouvait déranger l'utilisateur.
   - **Solution :** J'ai proposé une solution pour afficher un message par défaut, comme "Aucun détail disponible pour cette réponse", si `answerDetail` est vide. Cela améliore l'expérience utilisateur.
2. **Utilisation des computed properties dans `QuestionRadio.vue`** :

   - **Difficulté :** J'ai eu du mal à bien comprendre comment lier les options à la réponse correcte et afficher la bonne valeur.
   - **Solution :** Après avoir utilisé `find()` dans le computed property, j'ai pu récupérer le texte de la réponse correctement, même si l'utilisateur avait sélectionné une option dans une liste.

3. **Problèmes de CSS avec les couleurs de texte** :
   - **Difficulté :** Les couleurs des textes n'étaient pas appliquées comme prévu. J'ai dû demander à Chat pour avoir les références des couleurs.

## Explications et réflexions sur le code

1. **Pourquoi avoir ajouté la propriété `answerDetail` dans `QuestionText.vue` ?**

   - L'objectif était de fournir plus de détails à l'utilisateur lorsqu'il obtient une réponse incorrecte, afin qu'il puisse mieux comprendre pourquoi sa réponse est fausse. Cela permet aussi de renforcer l'apprentissage en expliquant la bonne réponse.

2. **Pourquoi utiliser `v-if` et `v-else` dans le template ?**

   - J'ai utilisé `v-if` et `v-else` pour afficher différentes informations en fonction de la validité de la réponse. Si la réponse est correcte, le message est affiché en vert avec "Juste !", sinon un message d'erreur est affiché en rouge avec la réponse correcte.

3. **Pourquoi utiliser des styles scoped dans Vue ?**
   - L'utilisation de `scoped` permet de limiter l'application des styles uniquement au composant en question, ce qui évite les conflits de styles avec d'autres parties de l'application.

## Réponses aux questions

**Que se passe-t-il lorsqu'on ne met pas de valeur à answer-detail ?**

Quand on ne met pas de valeur à answerDetail, la valeur par défaut définie dans le code est utilisée. VU qu'on met rien comme valeur (''), il n'y aura rien qui s'affiche à l'écran.

**Est-ce satisfaisant ?**
Pas vraiment. Si l'utilisateur a une mauvaise réponse, il pourrait s'attendre à voir une explication ou un détail pour comprendre son erreur. Mais là, il ne voit rien, ce qui peut être frustrant ou déroutant.

**Proposition d'amélioration**
Si answerDetail est vide, on peut mettre comme texte : 'Pas d'explication possible."
Sinon, afficher le texte normal de answerDetail.

# Journal de Bord - Semaine 6

## Temps estimé et temps passé

- **Temps estimé :** 6 heures
- **Temps passé :** 7 heures
  J'ai fait le ce qu'il faillait faire en classe en 1 heure.

## Lien Github
https://hepl-bs21inf5.github.io/sem07-project-alphone13/

## Notes concernant les améliorations

Au début, de chaque nouvelles améliorations (pour les composants) je prenais exemple sur le mauvais composant. Ce qui fait que j'ai passé énormément de temps à essayer de lier deux composants (parents?). Par exemple pour QuestionSelect.vue je me suis inspiré de QuizForm.vue au lieu de QuestionCheckBox par exemple. Ce qui fait que quand je voulais importer QuestionSelect.vue dans QuizForm.vue il y avait des beug. C'est après de longues heures à me tromper que j'ai bien compris qu'il fallait faire attention aux liens qu'il y a entre les différents composants.

Exemple d'erreur:
J'ai commencé à améliorer Trivia.Vue et les boutons réinitialiser et terminer ne marchaient pas, alors que j'avais repris le code de QuizForm qui lui marchait. Il fallait que je puisse bien initialiser les constante et en plus adapter la logique des méthodes. Le reste restait pareil que dans QuizForm.
Aussi j'ai modifié la partie avec le fetch.

Code des méthodes de QuizForm :

```JS
function submit(event: Event): void {
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Submit)
}

function reset(event: Event): void {
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Empty) //on met l'état des réponses à vide.
}
```

Alors QuizForm est un composant parent où il y a toutes les importations.
Je voulais implémenter des functions dans `QuestionSelect.vue` comme QuiForm et ça créait des conflits lors des importations.

J'ai donc corrigé en prenant le code de depuis `QuestionCheckbox.vue`:
Code de `QuestionCheckbox.vue`:

```JS
function submit(event: Event): void {
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Submit)
}

function reset(event: Event): void {
  event.preventDefault()
  questionStates.value = questionStates.value.map(() => QuestionState.Empty) //on met l'état des réponses à vide.
}
```

## Tâches réalisées

1. **Déploiement sur GitHub Pages** :  
   D'abord j'ai configuré GitHub Pages pour le projet. J'ai changé la visibilité du dépôt en public et configuré GitHub Actions pour que le site soit automatiquement construit et déployé sur GitHub
   Ensuite, j'ai créé le fichier `.github/workflows/deploy.yml` pour définir la configuration de déploiement avec GitHub Actions.

   - Lien GitHub https://hepl-bs21inf5.github.io/sem07-projet-alphone13/

2. **Modification du fichier `vite.config.ts`** :

   - J'ai ajouté le chemin de base pour GitHub Pages dans le fichier `vite.config.ts` en définissant la base à `/sem07-project-alphone13/`. Cela permet de résoudre le problème de la page blanche sur le site déployé.
   - **Code modifié :**
     ```typescript
     export default defineConfig({
       base: '/sem07-project-{pseudo}/',
       plugins: [vue(), vueDevTools()],
       resolve: {
         alias: {
           '@': fileURLToPath(new URL('./src', import.meta.url)),
         },
       },
     })
     ```

3. **Amélioration de `QuestionCheckbox.vue`** :

   - J'ai ajouté la possibilité de sélectionner plusieurs réponses à l'aide du composant `QuestionCheckbox.vue` dans `QuizForm.vue`, ce qui permet de mieux gérer les questions où plusieurs options peuvent être correctes.

4. **Nettoyage et vérification du projet** :
   - J'ai vérifié l'ensemble du projet pour m'assurer qu'il n'y avait pas de code inutile. J'ai également vérifié en exécutant `npm run build` que le code fonctionne correctement.
   - **Vérification en ligne :** Le site a été testé sur plusieurs appareils (ordinateur et téléphone) pour garantir qu'il s'affiche correctement partout.

## Difficultés rencontrées et solutions trouvées

1. **Problème avec les imports et redémarrage du projet** :
   - **Difficulté :** J'ai rencontré un problème lors du déploiement du projet, où il fallait souvent recommencer certaines étapes à chaque fois, notamment à cause de problèmes liés aux imports dans le fichier `vite.config.ts` et d'autres fichiers de configuration.
   - **Solution :** J'ai dû m'assurer que tous les imports étaient correctement configurés et vérifier plusieurs fois les chemins d'accès. J'ai aussi réinitialisé le projet et fait plusieurs essais (en effaçant parfois complétement le code et en reprenant étapes par étapes) pour m'assurer que tout fonctionnait correctement avant de procéder au déploiement.

## Explications et réflexions sur le code de `QuestionCheckbox.vue`

Dans QuestionCheckbox:

```JS
watch(model, (newModel) => {
  if (newModel === QuestionState.Submit) {
    const isCorrect = //J'aurai pu aussi trier les deux listes et ensuite les comparer
      props.answer.length === value.value.length &&
      props.answer.every((val) => value.value.includes(val))
    model.value = isCorrect ? QuestionState.Correct : QuestionState.Wrong
  } else if (newModel === QuestionState.Empty) {
    value.value = []
  }
})
```

Les 3 lignes props.answer.length === value.value.length && props.answer.every((val) => value.value. et model.value = isCorrect ? QuestionState.Correct : QuestionState.Wrongincludes(val)) ont été faite avec ChatGPT,car je n'avais pas compris qu'il fallait comparer les valeurs entre elles et les écrire de la sorte.

1. **Pourquoi avoir choisi l'amélioration de `QuestionCheckbox.vue` ?**

   - L'amélioration de `QuestionCheckbox.vue` permet de gérer des questions où plusieurs réponses sont possibles. Cela rend le quiz plus flexible et plus proche de certaines questions de type "vrai/faux" ou "plusieurs bonnes réponses", ce qui est souvent utilisé dans des quiz plus complexes.

2. **Comment avez-vous implémenté cette amélioration ?**

   - J'ai modifié le composant `QuestionCheckbox.vue` en m'inspirant de `QuestionRadio.vue` pour que l'utilisateur puisse sélectionner plusieurs cases au lieu d'une seule. J'ai ajusté le modèle de données et la logique de validation pour accepter plusieurs réponses, puis j'ai testé le composant pour m'assurer qu'il fonctionnait comme prévu.

3. **Quels problèmes avez-vous rencontrés lors de l'implémentation de cette amélioration ?**

   - L'un des problèmes majeurs a été de m'assurer que le composant gérait correctement la sélection de plusieurs cases et que la validation était bien faite sur toutes les réponses sélectionnées. J'ai dû passer un peu de temps à tester différents cas pour garantir qu'aucune réponse incorrecte ne passait. Aussi je devais m'assurer que ce type de question était pris en compte dans le score.

4. **Quelles améliorations pourriez-vous encore apporter dans `QuestionCheckbox.vue` ?**

   - Je pourrais améliorer le code pour avoir une meilleure gestion des erreurs utilisateur (par exemple, prévenir l'utilisateur si aucune réponse n'est sélectionnée) pourrait être ajoutée.

5. **Amélioration de QuizTrivia**
   Ancien code fetch de QuizTrivia:

```JS
fetch('https://opentdb.com/api.php?amount=10&type=multiple')
  .then((response) => response.json())
  .then((data) => (questions.value = data.results))
```

Nouveau code fetch de QuizTrivia qui est maintenant une fonction:

```JS
function fetchQuestions(): void {
  questions.value = []
  questionStates.value = [] // Réinitialiser les états
  fetch('https://opentdb.com/api.php?amount=10&type=multiple')
    .then((response) => response.json())
    .then((data) => {
      questions.value = data.results.map((q: { correct_answer: any; incorrect_answers: any[]; }) => ({
        ...q,
        shuffledAnswers: shuffleArray([
          { value: q.correct_answer, text: q.correct_answer },
          ...q.incorrect_answers.map((answer: any) => ({
            value: answer,
            text: answer,
          })),
        ]),
      }))
      // Initialiser tous les états à "Empty"
      questionStates.value = new Array(data.results.length).fill(QuestionState.Empty)
    })
}
```

Cette version récupère comme la précédente les questions via l'API.

L'ancienne version se contentait de récupérer les questions via l'API avec fetch et stockaient les variable dans question.value.

J'ai également ajouté cette méthode:

```JS
// Charger les questions au démarrage
fetchQuestions()
```

Qui permet de charger les questions au démarrage.

La nouvelle version initialise question.value dans un tableau de questions (qui est ici data.results). Le data.results est lui initialisé à QuestionState.Empty qui fait que les réponses soient vides au début.

### Amélioration de la fonctionnalité dans `QuestionSelect.vue`

#### Pourquoi ai-je choisi cette amélioration ?

J'ai choisi cette approche car elle est simple et très adaptée à un formulaire de quiz où l'utilisateur doit choisir une réponse parmi plusieurs options. Avant cette modification, l'utilisateur était limité dans le choix de ses réponses, ce qui ne convenait pas à tous les types de questions, notamment celles où l'on attendait une réponse sélectionnée dans une liste déroulante. En ajoutant la possibilité de sélectionner une réponse parmi plusieurs dans un menu déroulant, on simplifie l'interaction et on améliore l'accessibilité.

### Temps estimé et temps passé sur le projet

**Temps estimé** : J'avais estimé que cela me prendrait environ 1 heure pour implémenter le composant `QuestionSelect.vue` et l'intégrer dans le projet, étant donné que je devais aussi gérer les états et l'interaction avec le formulaire.

**Temps passé** : En réalité, j'ai mis environ 3 heures pour finaliser le composant. Cela m'a pris un peu plus de temps que prévu car j'ai dû tester plusieurs aspects du composant (comme les options de réponse, la gestion des états et la réactivité) pour m'assurer que tout fonctionnait correctement. De plus, je n'avais pas lié correctement les composants pour avoir un bon fonctionnement.

### Tâches réalisées

- **Création du composant `QuestionSelect.vue`** : J'ai développé un composant permettant de gérer une question de type "sélection" avec un menu déroulant (`<select>`) se trouvant dans le template.
  Voici un extrait de code pour expliquer cela :

  ```HTML
  <template>
    <select v-model="selectedAnswer">
      <option v-for="(option, index) in options" :key="index" :value="option.value">
        {{ option.label }}
      </option>
    </select>
  </template>
  ```

- **Ajout de la logique pour l'affichage des réponses** : J'ai implémenté la logique pour afficher des messages lorsque la question est soumise, en indiquant si la réponse est correcte ou incorrecte. J'ai aussi ajouté un message détaillant pourquoi la réponse est correcte ou incorrecte, basé sur la `answerDetail` passée en prop:

```HTML <p class="blockquote-footer">{{ props.answerDetail }}</p> ````

- **Désactivation du menu déroulant après soumission** : Le menu de sélection est désactivé une fois que la réponse a été donnée, ce qui évite que l'utilisateur puisse modifier sa réponse après soumission.

- **Tests et intégration avec le `QuizForm`** : J'ai testé le composant dans le contexte du formulaire du quiz, en l'intégrant dans le code existant pour m'assurer qu'il interagit bien avec les autres composants et que les réponses sont correctement gérées.

### Explications et réflexions sur le code de `QuestionSelect.vue`

#### Comment l'ai-je implémentée ?

Pour implémenter cette fonctionnalité, j'ai d'abord analysé le composant `QuestionSelect.vue`, qui était déjà en place pour gérer une seule option. L'objectif était de lui permettre de traiter une liste d'options, afin que l'utilisateur puisse choisir parmi une liste déroulante. J'ai utilisé `QuestionState` pour définir clairement les différents états possibles de la question, ce qui aide à la gestion de l'affichage des résultats.
Voici les étapes que j'ai suivies :

1. **Modification de la structure des données :** J'ai ajusté les données de la question pour qu'elles incluent une liste d'options à afficher dans le sélecteur. Cela signifie que, pour chaque question de type `QuestionSelect`, il faut maintenant une clé supplémentaire avec un tableau d'options.

2. **Mise à jour du template :** J'ai utilisé la balise `<select>` en HTML pour créer un menu déroulant. À l'intérieur de cette balise, j'ai utilisé la directive `v-for` pour afficher dynamiquement chaque option à partir du tableau d'options.

3. **Gestion de la réponse sélectionnée :** J'ai lié le modèle `v-model` à une variable `selectedAnswer`, afin de capturer la réponse de l'utilisateur et la comparer à la réponse correcte de la question. Cela permet une gestion facile et réactive des choix de l'utilisateur.

4. **Validation de la réponse :** Une fois que l'utilisateur a sélectionné une réponse, j'ai intégré une logique de validation pour comparer la réponse choisie à la réponse correcte. Si la réponse est correcte, un message de confirmation apparaît, sinon un message d'erreur est affiché.

#### Quels problèmes ai-je rencontrés ?

L'un des défis majeurs a été de m'assurer que le composant `QuestionSelect.vue` fonctionne correctement avec les autres composants du quiz, notamment ceux qui gèrent la validation des réponses et le passage à la question suivante.

- **Problème de désactivation des menus déroulants :** J'avais oublié de désactiver le menu déroulant une fois la réponse donnée. J'ai corrigé cela en utilisant la condition sur `model` pour désactiver les éléments lorsque la question est soumise ou la réponse est correcte/incorrecte.

- **Difficulté avec l'intégration du composant :** Quand j'ai intégré le composant dans `QuizForm`, je me suis rendu compte qu'il y avait quelques soucis avec les props, notamment avec la gestion des options et des réponses. J'ai résolu ce problème en m'assurant que les données passées au composant étaient bien formatées et en vérifiant que les bonnes valeurs étaient liées aux réponses dans `v-model`.

**Ordre aléatoire des choix dans QuestionRadio.vue.**

J'ai ajouté une fonction shuffleArray qui mélange aléatoirement les options une seule fois, et ce, au moment où le composant est monté.

Voici le code que j'ai ajouté:

```JS
// Mélanger un tableau
function shuffleArray<T>(array: T[]): T[] {
  const shuffled = [...array];
  for (let i = shuffled.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];  // échange
  }
  return shuffled;
}

```

Cette fonction mélange un tableau aléatoirement. Elle fonctionne en parcourant le tableau de la fin vers le début, en échangeant chaque élément avec un autre élément choisi aléatoirement avant lui.

cette fonction va avec:

```JS
onMounted(() => {
  shuffledOptions.value = shuffleArray(props.options);  // Mélange une seule fois les options
});
```

Cette fonction garantit que l'ordre des options est mélangé une seule fois au début, et qu'il reste fixe pendant que l'on effectue le quiz.

Pour pouvoir utiliser ces deux fonctions il faut d'abord initialiser ShuffledOptions:

```JS
const shuffledOptions = ref<{ value: string; text: string }[]>([]);
```

je l'ai initialisé en la mettant comme une référence réactive qui stocke les options mélangées.

Puis dans le `template`, j'ai remplacé ça :

```JS
<div v-for="option in props.options" :key="option.value" class="form-check">
```

par:

```JS
<div v-for="option in shuffledOptions" :key="option.value" class="form-check">

```

Cela fait en sorte que les options affichées soient issues de la variable qui contient l'ordre mélangé et garanti qu'elles restent dans cet ordre pendant l'interaction.

### Améliorations de style

Il y a deux façons de changer de style :

1. Depuis main.css

2. avec <style scoped>

   - se fait directement dans le composant

La différence est qu'avec main.css, il faut ajouter 'class=""', avec le nom du style. Par exemple:

```HTML
<p class="question-title">Question 6</p>
```

et class fait appel à:

```CSS
.question-title {
  font-family: 'Arial', sans-serif; /* Choisir une police de caractères */
  font-size: 1.5rem; /* Taille du texte */
  font-weight: bold; /* Mettre en gras */
  color: #ff66b2; /* Couleur du texte */
  margin-bottom: 10px; /* Espacement en bas */
}
```

qui se situe dans main.css. L'avantage avec main.css est qu'on modifie directement le style et il s'applique à toutes les pages souhaitées. Avec style scoped, l'avantage est que si on veut appliquer un style différent à chaque page on peut. Le problème est plus dans l'organisation du code où ça ajoute des lignes de code en plus.

#### Explications de main.css

```CSS
.container {
  background-color: #f6e1f2; /* Fond rose clair très doux */
  padding: 25px; /*Ajoute des espaces sur les bords latéraux*/
  border-radius: 12px; /*Arrondis*/
  box-shadow: 0 5px 12px rgba(0, 0, 0, 0.1); /*effet ombre*/
}
```

définit le style général du conteneur du quiz, donc la zone qui entoure tout le contenu du quiz.

Le code de l'écriture du titre:

```CSS
.quiz-title {
  font-family: 'Arial', sans-serif;
  font-size: 2.2rem;
  font-weight: bold;
  color: #862d7e; /* Violet foncé */
  text-align: center;
  margin-bottom: 15px;
}
```

personnalise l'apparence du texte ayant la classe `.quiz-title` : il lui donne une police spécifique, une taille de texte assez grande, la rend en gras, change la couleur et centre le texte.

Pour les boutons :

```CSS
.btn {
  --bs-btn-color: #a83b9e; /* Texte violet foncé */
  --bs-btn-border-color: #ff66b2; /* Bordure rose vif */
  --bs-btn-focus-shadow-rgb: 255, 153, 204; /* Ombre rose doux au focus */
  --bs-btn-active-shadow: inset 0 3px 6px rgba(255, 102, 178, 0.2); /* Ombre interne légère rose */
}
```

Ce bout de code personnalise l'apparence d'un bouton en définissant des couleurs pour le texte, la bordure, l'ombre au focus et l'ombre interne active avec des tons de violet et de rose.
j'ai hiérarchisé pour appliquer un style différent à chaque bouton, mais le fonctionnment est le même pour les boutons info, primary et secondary.

# Choix des Améliorations

**Pourquoi avez-vous choisi ces améliorations ?**

**Comment les avez-vous implémentées ?**
J'ai implémenté les différentes améliorations en m'inspirant principalement du code des composants réalisés en classe (en m'inspirant par exemple de Questionradio pour faire QuestionSelect). Je me suis également documentée sur Vue.js pour approfondir mes connaissances.

**Quels problèmes avez-vous rencontrés ?**
Pendant que je faisais le projet j'avais perdu de vue que QuizForm était le composant principal (parent) et que pour créer d'autres composants, il ne fallait pas s'inspirer de lui pour faire les autres composants.

#### Quelles améliorations pourrais-je encore apporter ?

Pour **QuizForm**:
je pense que j'aurais pu éviter de faire des répétitions dans le code. Aussi j'aurais pu ajouter des messages et des images qui s'affichent quand toutes les qestions n'ont pas été répondues. Ou encore j'aurais pu ajouter des messages et des images qui s'affichent quand on répond aux questions.

Pour **Ordre aléatoire des choix dans QuestionRadio.vue.**;
J'aurais pu faire en sorte que quand on clique sur le bouton réinitialiser, les options des réponses se mélangent.

Pour **QuizTrivia et QuizForm**
J'aurais pu par exemple intégrer une barre de progression pour visualiser l’avancement lors du remplissage du quiz.

**Pour le style glogal du quiz**:
J'aurais pu mettre la barre de navigation (navbar) en rose comme le reste de mon quiz.

# Pour conclure le projet

J'ai appris à créer une page web
### Notes de compréhension

Que veut dire qu'un code est plus dynamique?:

Un code est plus dynamique lorsqu'il interagit avec l'utilisateur, réagit aux changements ou adapte son comportement en fonction de divers facteurs (données,environnements,conditions,...).
Props: sert à communiquer avec le composant parent
