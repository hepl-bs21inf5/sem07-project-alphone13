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

### réponses aux questions de la semaine 1

Les rôles :
main.ts : TypeScript
mains.css: Permet de gérer le style de la page HTML
App.vue: Permet de modifier le types de barre de navigation ainsi que le logo clickable pour naviguer sur différentes pages.
router/index.ts:
Aboutview.vue:
HomeView.vue : document HTML contenant le titre et affiche le titre
QuizForm.vue : Permet de créer la page de quiz avec les question et réponses en HTML et Javascript

Dans le fichier QuizForm.vue :

Quelles sont les similarités et les différences entre ref et computed ?

REF: est ulisisé pour les valeurs réactives. Les valeurs qu'il retourne ont une propriété .value et si la valeur est un objet vue.js le met automatiquement à jour.

COMPUTED: C'est une fonction qui permet de calculer dynamiquement une valeur en fonction des données existantes. il ,met aussi à jour les valeurs en cas de modifications. valeur dérivée

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

# réponse questons de la semaine 2 : à répondre

Quelle est la différence entre un prop et un modèle (v-model) ?

Comment rendre la propriété placeholder optionnelle ?

# commentaires

On a créer une version plus compacte du code. Ce qui est en commentaire à la fin est lancienne version qui marche, mais bien plus logue en matière de code.
On a modifier le code pour le calcul du score.

## 21.11.2024

temps:
temps destimation : 75 min
temps réel: 65 min

Cette fois-ci j'ai cru que j'allais passé plus de temps, car je ne comprenais pas au début ce qui était demandé. Mais en demandant de laide j'ai pu surpasser cette difficulté.

# Réponses aux questions

À quoi sert l'option immediate: true dans le watch ? Que se passe-t-il si on l'enlève ou si on met immediate: false ?

Proposer une autre manière de calculer le score et comparer les deux méthodes.
