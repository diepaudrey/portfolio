<template>
  <transition appear @before-enter="beforeEnter" @enter="enter">
    <div
      :class="{
        'picture-container': true,
        'second-picture': isDivisibleByThree(index + 1),
        'third-picture': isDivisibleByThree(index)
      }"
    >
      <img :src="`/assets/gallery/${image.name}`" :alt="image.title" loading="lazy" />
      <div class="overlay">
        <h2>{{ image.title }}</h2>
        <p>{{ image.date }}</p>
      </div>
    </div>
  </transition>
</template>

<script>
import gsap from 'gsap'
export default {
  setup(props) {
    const beforeEnter = (el) => {
      el.style.opacity = 0
      el.style.transform = 'translateY(60px)'
    }
    const enter = (el) => {
      gsap.to(el, {
        opacity: 1,
        y: 0,
        duration: 3,
        ease: 'slow(0.7,0.7,false)',
        delay: props.index * 0.2
      })
    }
    return { beforeEnter, enter }
  },
  props: {
    image: { type: Object, required: true },
    index: { type: Number, required: true }
  },
  methods: {
    isDivisibleByThree(num) {
      return num % 3 === 0
    }
  }
}
</script>

<style scoped>
@media screen and (max-width: 480px) {
  .picture-container {
    justify-content: center;
    width: 80%;
    aspect-ratio: 1;
    img {
      display: block;
      border-radius: 25px;
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
    border-radius: 25px;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}
@media screen and (min-width: 481px) and (max-width: 1023px) {
  .picture-container {
    position: relative;
    width: 40vw;
    height: 40vw;
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
}
@media screen and (min-width: 1024px) {
  .picture-container {
    width: 25vw;
    height: 25vw;
    img {
      border-radius: 50px;
    }
  }

  .second-picture {
    margin-top: 10vh;
  }
  .third-picture {
    margin-top: 15vh;
  }
}
</style>
