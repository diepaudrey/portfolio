<template>
  <nav class="nav-container">
    <div class="nav-bar">
      <RouterLink to="/">About</RouterLink>
      <img src="../assets/logo.svg" alt="Minimalist sun design" />
      <RouterLink to="/gallery">Gallery</RouterLink>
    </div>
  </nav>
</template>

<script>
import { RouterLink } from 'vue-router'
</script>

<style scoped>
.nav-bar {
  display: flex;
  justify-content: center;
  align-items: start;
  animation: opacity 3s ease;
  img {
    margin-top: 8px;
  }
}
.nav-container {
  animation: folding 0.8s ease;
  height: 7vh;
  background-color: var(--vt-c-black);
  border-radius: 0 0 50px 50px;
  border-bottom: solid 2px rgba(129, 129, 129, 0.5);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.nav-container:hover {
  height: 10vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  animation: unfolding 0.8s ease;
}

@keyframes unfolding {
  0% {
    height: 7vh;
  }
  100% {
    height: 10vh;
  }
}

@keyframes folding {
  0% {
    height: 10vh;
  }
  100% {
    height: 7vh;
  }
}
</style>
