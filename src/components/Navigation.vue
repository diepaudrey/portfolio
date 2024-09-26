<template>
  <nav class="nav-container">
    <div class="nav-bar">
      <RouterLink to="/">About</RouterLink>
      <img src="../assets/logo.svg" alt="Minimalist sun design" />
      <RouterLink to="/gallery">Gallery</RouterLink>
    </div>
    <img class="splitter" src="../assets/splitter.svg" alt="Line splitting the nav bar" />
  </nav>
</template>

<script setup lang="ts">
import { RouterLink } from 'vue-router'
</script>

<style scoped>
.nav-bar {
  display: flex;
  justify-content: center;
  align-items: start;
  margin-top: 25px;
}
.nav-container {
  background-color: var(--vt-c-black);
  border-radius: 0 0 50px 50px;
  display: flex;
  flex-direction: column;
  align-items: center;
  .splitter {
    width: 95%;
  }
}
</style>
