# JOURNAL DE BORD

## 7.11.2024:

Tableau des heures passées:

| Tâche       | Temps estimé | passé |
| ----------- | ------------ | ----- |
| Ecriture du | 30m          | 45m   |
| code HTML   |
| CSS         | 10m          | 5m    |
| ...         | ...          | ...   |
| Total       | 1h10         | 2h30  |

Commentaires:

on a installé ce dont on avait besoin pour le projet avec l'aide du terminal.
Ce fût difficile d evoir où on faisait des erreurs, car parfois VSCode nous met les vagues rouges alors qu'il n'y a pas de fautes.

Pour les questions du quiz, j'ai copié-collé le template du cheval. et changé le script des autres questions, ainsi que leur score.
pour la question 2 : le nom est calcul

le template contient toutes les questions du quiz.

la page web ne saffichait pas dans le navigateur du coup, j'ai pris du retard.

### Réponses aux questions de la semaine 1

#### Les rôles :

main.ts : (TypeScript) vient initialiser l'application Vue et Monte l'application sur une partie spécifique de la page web (le DOM, qui est une représentation en mémoire de la page web et permet de modifier ou de lire une page web).

mains.css: Permet de gérer le style de la page HTML

App.vue: Permet de modifier le types de barre de navigation ainsi que le logo clickable pour naviguer sur différentes pages.

router/index.ts: sert à la configuration des routes (chemins urls). détermine quels éléments doivent être affichés sur l'application Vue

Aboutview.vue: Affiche le texte de l'index 'À propos'
HomeView.vue : document HTML contenant le titre et affiche le titre
QuizForm.vue : Permet de créer la page de quiz avec les question et réponses en HTML et Javascript

Dans le fichier QuizForm.vue :

Quelles sont les similarités et les différences entre ref et computed ?

#### REF:

est ulisisé pour les valeurs réactives. Les valeurs qu'il retourne ont une propriété .value et si la valeur est un objet vue.js le met automatiquement à jour.

#### COMPUTED:

C'est une fonction qui permet de calculer dynamiquement une valeur en fonction des données existantes. il, met aussi à jour les valeurs en cas de modifications. valeur dérivée

la diférence entre le ref réside dans les valeurs. Si une valeur peut être directement modifiée alors on utilise le ref

Que se passe-t-il lorsqu'on clique sur le bouton "Terminer" ?
Il permet de terminer le quiz et d'envoyer les réponses afin de vérifier si elles sont justes

Qu'est-ce qu'un v-model ?
C'est une commande qui permet de lier une donnée JavaScript et un élément HTML automatiquement. Par exemple, si il y a un chamgement de valeur dans le code HTML, il y a une mise à jour automatique dans le JavaScript.

À quoi sert le :class="{ disabled: !filled }" ?
Il sert à lier l'attribut class d'un élément HTML avec un élément du JavaScript et rend la class dynamique.

## 14.11.2024

Les heures passées à faire le projet
temps destimation : 40 min
temps réel: 72 min

### réponse questons de la semaine 2 : à répondre

Quelle est la différence entre un prop et un modèle (v-model) ?
Props: transmission des données parent vers enfant
v-model: Combine un prop et un événement. Lie un composant parent avec un composant enfant

Comment rendre la propriété placeholder optionnelle ?

### Commentaires

On a créer une version plus compacte du code. Ce qui est en commentaire à la fin est l'ancienne version qui marche, mais bien plus logue en matière de code.

Voici l'ancienne version du code :

```HTML
  <!-- Ancien code HTML qui prend bien plus de place-->
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

    partie 2 pour la 2ème question

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
  function resetquiz(): any {
    console.log('Le quizz a été réinitialisé')
  if (calcul.value == '10') {
    /*on a mis la valeur en str donc il faut aussi la mettre en str ici */
    score += 1
  }
  if (Eiffel.value == 'Paris') {
    score += 1
  }
```

## 21.11.2024

# Temps

temps destimation : 75 min
temps réel: 65 min

Cette fois-ci j'ai cru que j'allais passé plus de temps, car je ne comprenais pas au début ce qui était demandé. Mais en demandant de l'aide j'ai pu surpasser cette difficulté.

# Réponses aux questions

un watch est un handler. Il observe une donnée et quand la donnée change le watch s'exécute.

Un handler (ou gestionnaire en français) est une fonction ou un bloc de code que vous définissez pour répondre à un événement ou à une situation particulière (pris de Chat)

À quoi sert l'option immediate: true dans le watch ?
à executer la fonction de rappel watch et à synchroniser les données dès le départ. Réactivité des changement de valeur. Il faut que le watch soit configuré pour que immediate : true marche.

Que se passe-t-il si on l'enlève ou si on met immediate: false ?
Si on enlève immediate :false il se passera que le handler sera exécuté que lorsque la valeur surveillée/assignée change pour la première fois.

Proposer une autre manière de calculer le score et comparer les deux méthodes.

## 28.11.2024

# Temps

temps estimé : 45 min
temps réellement passé : 60 min

# Commentaires

On s'est occupé des réponses, en modifiant d'abord le script de QuestionRadio.

un watch sur value qui permet d'exécuter une fonction à chaque fois que value change

# Réponses aux questions

Comment pourrait-on réécrire la ligne suivante sans l'opérateur ternaire (avec des if et else) ?
model.value =
value.value === props.answer ? QuestionState.Correct : QuestionState.Wrong;

on peut le réecrire avec des if et else comme ça :

if (value.value === props.answer) {
model.value = QuestionState.Correct;
} else {
model.value = QuestionState.Wrong;
}

Comment pourrait-on réécrire autrement la logique du watch sur value ?

## 5.12.2024

# Commentaires

on a changé la forme du function submit et reset. Voici lancienne version:

```JS
function submit(event: Event): void {
event.preventDefault()
let score: number = 0
if (cheval.value === 'blanc') {
score += 1
}

if (calcul.value == '10') {
/_on a mis la valeur en str donc il faut aussi la mettre en str ici _/
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

cette version contient des conditions qui vérifient si la réponse est juste et additionne le score sous forme de condition.

La nouvelle verison est plus dynamique et plus compacte. Elle contient également les liens entre les différents composants

# Notes de code

```JS
const model = ref<
string | null

> () /_Le ref est utlisée pour les valeurs réactives (la valeur réactives va être suivie par vue.js) _/
> const cheval = ref<string | null>(null)
> const calcul = ref<string | null>(null)
> const eiffel = ref<string | null>(null)

qui va avec:
const filled = computed<boolean>(
/_On a mis du boolean à la place, c'est lié avecle bouton primary disabeld filled_/ () =>
cheval.value !== null && calcul.value !== null && eiffel.value !== null,
)
const correctAnswers = ref<boolean[]>([])

//AVANT : on cherchait à savoir si la réponse était juste avec des valeurs booléennes.

//Calcule le score total
const score = computed<number>(() => correctAnswers.value.filter((value) => value).length)
const totalScore = 3
```

# Notes de compréhension

le v-model= "something[0]", la valeur qui est entre crochets doit être dans un certain ordre. Il ne faut pas qu'il y ait des chiffres qui sautent/manquent.

Que veut dire qu'un code est plus dynamique?:
Un code est plus dynamique lorsqu'il interagit avec l'utilisateur, réagit aux changements ou adapte son comportement en fonction de divers facteurs (données,environnements,conditions,...)

# personnalisation

Bootstrap est correctement utilisé pour rendre l'application responsive.

# semaine 5 12.12.2024

J'ai modifié un peu la structure du code et j'ai modifié le CheckBox dans QuizForm.
il faut que jajoute des espaces entre les questions

Pour la question où il faut écrire soi-même la réponse, j'ai modifier answer (dansle QuizForm) afin qu'il puisse contenir une liste de réponses.

# temps

commencé à 10h15 et finis ce que qu'il fallait faire vers environ 11h30

j'ai passé du temps à répondre aux questions. Il faut que je revoie quel type de fonction est un immidiate et il faut que je fasse un résumé de tout ça.

## Réponses aux questions

là il faut que la string soit un élément contenu dans la liste

Que se passe-t-il lorsqu'on ne met pas de valeur à answer-detail ? Est-ce satisfaisant ? Si ce n'est pas le cas, proposer une amélioration.

# Prise de notes

dans QuestionText
model.value = props.answer.includes(value.value ?? "") ? QuestionState.Correct : QuestionState.Wrong;
ce que fait cette ligne : elle vérifie si la valeur donnée se trouve dans la liste définie dans QuizForm.vue. props.answer.includes(value.value ?? "") regarde si la réponse mise est vide et si la réponse est vide elle va la considérer comme une chaîne de caractère vide.

## 19.12.2024

fait des modifications au niveau des couleurs de la page web. Demander pk TRivia vmodel beug hahaha.
ajouter une image et faire les bootstaps

# Temps

commencé à 10h00
fini ce qu'il fallait faire (en tous cas le minimum) à 11h20

# Réponses aux questions

visualiser le rapport ctr maj v

# Lien GitHub

https://hepl-bs21inf5.github.io/sem07-projet-{alphone13]/
