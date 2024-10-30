<template>
  <div class="main-container">
    <transition name="fade-left">
      <div class="title-container" v-show="showTitle">
        <img src="../assets/graphic2.svg" alt="Minimalist Graphic Design" />
        <h1>Gallery</h1>
      </div>
    </transition>
    <div class="gallery">
      <div
        v-for="(image, key) in gallery"
        :class="{
          'end-position': isEvenNumber(Number(key))
        }"
      >
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
      showTitle: false,
      gallery: {} // Initialiser une propriété gallery vide
    }
  },
  mounted() {
    setTimeout(() => {
      this.showTitle = true
    }, 1)

    this.gallery = galleryData
  },
  methods: {
    isEvenNumber(num) {
      return num % 2 === 0
    }
  }
}
</script>

<style scoped>
@media screen and (max-width: 480px) {
  .title-container {
    justify-content: end;
    img {
      width: 45%;
    }
  }
  .main-container {
    display: flex;
    flex-direction: column;
  }
  .gallery {
    display: grid;
    row-gap: 2%;
  }
  .gallery > div {
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
@media screen and (min-width: 481px) and (max-width: 1023px) {
  .title-container {
    width: 100%;
    display: flex;
    justify-content: end;
  }

  .main-container {
    display: flex;
    flex-direction: column;
  }
  .gallery {
    display: grid;
    row-gap: 5%;
    grid-template-columns: repeat(2, 1fr);
    justify-items: center;
  }

  .end-position {
    padding-top: 5vh;
  }
}

@media screen and (min-width: 1024px) {
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
}
</style>
