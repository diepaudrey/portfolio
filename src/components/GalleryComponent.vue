<template>
  <div class="main-container">
    <transition name="fade-left">
      <div class="title-container" v-show="showTitle">
        <img src="../assets/graphic2.svg" alt="Minimalist Graphic Design" />
        <h1>Gallery</h1>
      </div>
    </transition>
    <div class="gallery">
      <div v-for="(image, key) in gallery">
        <Picture :image="image" :index="Number(key)" />
      </div>
    </div>
  </div>
</template>

<script>
import galleryData from '../assets/gallery.json'
import Picture from './Picture.vue'

export default {
  components: {
    Picture
  },
  data() {
    return {
      showTitle : false,
      gallery: {} // Initialiser une propriété gallery vide
    }
  }, 
  mounted() {
    setTimeout(()=> {
      this.showTitle = true
    }, 1)

    this.gallery = galleryData
  }
}
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
