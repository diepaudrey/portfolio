<template>
  <transition name="fade-right">
    <div class="title-container" v-show="showTitle">
      <h1>Design</h1>
      <img src="../assets/graphic2.svg" alt="Minimalist Graphic Design" />
    </div>
  </transition>
  <div class="grid">
    <div v-for="(design, key) in designData">
      <Design :design="design" :index="Number(key)" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'
import designData from '../assets/design.json'
import Design from './Design.vue'

const showTitle = ref(false)
onMounted(() => {
  setTimeout(() => {
    showTitle.value = true
  }, 1)
})
</script>

<style scoped>
@media screen and (max-width: 480px) {
  .title-container {
    display: flex;
    padding: 2% 0 2% 5%;
    img {
      width: 45%;
    }
  }
  .grid {
    display: grid;
    row-gap: 2%;
    padding: 2%;
  }
}
@media screen and (min-width: 481px) and (max-width: 1023px) {
  .title-container {
    display: flex;
    padding: 2% 0 2% 5%;
  }
  .grid {
    display: grid;
    row-gap: 2%;
    padding: 2%;
  }
}
@media screen and (min-width: 1024px) {
  .title-container {
    padding: 2% 0 2% 5%;
  }
  .grid {
    display: grid;
    row-gap: 2%;
    padding: 2%;
  }
}
</style>
