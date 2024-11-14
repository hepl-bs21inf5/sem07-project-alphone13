<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>
<!--là c'est pour modifier la barre de navigation et les logos qui vont avec-->
<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <RouterLink class="navbar-brand" to="/">
        <i class="bi bi-alexa"></i>
        <!--là on a modifié licône du logo qui s'affiche à côté de quiz-->
        Quiz
      </RouterLink>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbar"
        aria-controls="navbar"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div id="navbar" class="collapse navbar-collapse">
        <ul class="navbar-nav">
          <li class="nav-item">
            <RouterLink class="nav-link" to="/about">
              <i class="bi bi-patch-question"></i>
              À propos
            </RouterLink>
          </li>
          <li class="nav-item">
            <RouterLink class="nav-link" to="/trivia">
              <i class="bi bi-question"></i>
              Trivia
            </RouterLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <RouterView />
</template>
