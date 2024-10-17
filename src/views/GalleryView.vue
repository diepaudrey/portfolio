<template>
  <section class="view">
    <Navigation />
    <GalleryComponent />
  </section>
</template>

<script setup>
import Navigation from '../components/Navigation.vue'
import GalleryComponent from '../components/GalleryComponent.vue'
</script>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
