<template>
  <transition appear @before-enter="beforeEnter" @enter="enter">
    <div class="main-container">
      <div class="picture-container" v-show="showPicture">
        <img
          :src="`/assets/projects/${props.project.illustration}`"
          alt="project illustration"
          loading="lazy"
        />
        <div class="overlay" @click="openProject">
          <h2>Check {{ props.project?.title }}</h2>
        </div>
      </div>

      <div class="text">
        <h2 class="text-link" @click="openProject">{{ props.project.title }}</h2>
        <p>
          {{ props.project?.description }}
        </p>
      </div>
    </div>
  </transition>
</template>

<script setup lang="ts">
import gsap from 'gsap'
import { onMounted, ref } from 'vue'

const props = defineProps({
  project: {
    type: Object,
    default: {
      '0': {
        title: 'Default Project',
        description: 'This is the default description of the project.',
        url: 'https://github.com/diepaudrey',
        illustration: 'logo.svg'
      }
    }
  },
  index: {
    type: Number,
    default: 0
  }
})

let picture = ref(0)
const beforeEnter = (picture: any) => {
  picture.style.opacity = 0
  picture.style.transform = 'translateY(60px)'
}
const enter = (picture: any) => {
  gsap.to(picture, {
    opacity: 1,
    y: 0,
    duration: 3,
    ease: 'slow(0.7,0.7,false)',
    delay: props.index * 0.5
  })
}
const showPicture = ref(false)
onMounted(() => {
  setTimeout(() => {
    showPicture.value = true
  }, 1)
})

const openProject = () => {
  window.open(props.project?.url, '_blank')
}
</script>

<style scoped>
@media screen and (max-width: 480px) {
  .picture-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 150px;
    width: 300px;
    border-radius: 25px;
    overflow: hidden;
    img {
      object-fit: cover;
      width: 100%;
    }
  }
  .main-container {
    display: flex;
    flex-direction: column;
    justify-content: start;
    padding: 0 3% 0 3%;
  }
  .text {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 3%;
    p {
      width: 80%;
    }
  }

  .overlay {
    position: absolute;
    opacity: 0;
  }
}
@media screen and (min-width: 481px) and (max-width: 1023px) {
  .picture-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 300px;
    width: 100%;
    border-radius: 25px;
    overflow: hidden;
    img {
      object-fit: cover;
      width: 100%;
    }
  }
  .main-container {
    display: flex;
    flex-direction: column;
    justify-content: start;
    padding: 0 3% 0 3%;
  }
  .text {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 3%;
    p {
      width: 80%;
    }
  }

  .overlay {
    position: absolute;
    opacity: 0;
  }
}
@media screen and (min-width: 1024px) {
  .picture-container {
    height: 500px;
    img {
      border-radius: 50px;
      width: 45vw;
    }
  }
  .main-container {
    display: flex;
    flex-direction: row;
    justify-content: start;
    padding: 0 3% 0 3%;
  }
  .text {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 3%;
    p {
      width: 80%;
    }
  }

  .overlay:hover {
    animation: color 2s ease;
    color: var(--red);
    cursor: pointer;
  }
}
</style>
