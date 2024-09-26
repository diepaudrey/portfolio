<template>
  <div
    :class="{
      'picture-container': true,
      'second-picture': isDivisibleByThree(props.index + 1),
      'third-picture': isDivisibleByThree(props.index)
    }"
  >
    <img :src="`/assets/gallery/${props.image.name}`" :alt="props.image.title" />
    <div class="overlay">
      <h2>{{ props.image.title }}</h2>
      <p>{{ props.image.date }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  image: { type: Object, required: true },
  index: { type: Number, required: true }
})

const isDivisibleByThree = (num: number) => {
  return num % 3 === 0
}
</script>

<style scoped>
.picture-container {
  position: relative;
  width: 25vw;
  height: 25vw;
  img {
    display: block;
    border-radius: 50px;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}

.picture-container:hover .overlay {
  opacity: 1;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: opacity 0.3s ease;
  background-color: rgba(0, 0, 0, 0.8);
  border-radius: 50px;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.second-picture {
  margin-top: 10vh;
}
.third-picture {
  margin-top: 15vh;
}
</style>
