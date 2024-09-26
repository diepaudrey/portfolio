<template>
  <div class="main-container">
    <div class="title-container">
      <img src="../assets/graphic2.svg" alt="Minimalist Graphic Design" />
      <h1>Gallery</h1>
    </div>
    <div class="gallery">
      <div v-for="(image, key) in gallery">
        <Picture :image="image" :index="Number(key)" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import gallery from '../assets/gallery.json'
import Picture from './Picture.vue'
</script>

<style scoped>
.title-container {
  width: 100%;
  display: flex;
  justify-content: end;
  padding-right: 5%;
}

.main-container {
  display: flex;
  flex-direction: column;
}

.gallery {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  justify-items: center;
}
</style>
