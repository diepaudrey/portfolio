<template>
  <transition appear @before-enter="beforeEnter" @enter="enter">
    <div class="design-container-desktop" v-if="props.index % 2 !== 0">
      <div :class="`picture-container ${props.design.size}`" v-show="showPicture">
        <img
          :src="`/assets/design/${props.design.illustration}`"
          alt="project illustration"
          loading="lazy"
        />
      </div>

      <div class="text">
        <h2>{{ props.design.title }}</h2>
        <p>
          {{ props.design?.description }}
        </p>
      </div>
    </div>
    <div class="design-container-desktop" v-else>
      <div class="text">
        <h2>{{ props.design.title }}</h2>
        <p>
          {{ props.design?.description }}
        </p>
      </div>
      <div :class="`picture-container ${props.design.size}`" v-show="showPicture">
        <img
          :src="`/assets/design/${props.design.illustration}`"
          alt="project illustration"
          loading="lazy"
        />
      </div>
    </div>
  </transition>

  <transition appear @before-enter="beforeEnter" @enter="enter">
    <div class="design-container-mobile">
      <div :class="`picture-container ${props.design.size}`" v-show="showPicture">
        <img
          :src="`/assets/design/${props.design.illustration}`"
          alt="project illustration"
          loading="lazy"
        />
      </div>

      <div class="text">
        <h2>{{ props.design.title }}</h2>
        <p>
          {{ props.design?.description }}
        </p>
      </div>
    </div>
  </transition>
</template>

<script setup lang="ts">
import gsap from 'gsap'
import { onMounted, ref } from 'vue'

const props = defineProps({
  design: {
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
</script>

<style scoped>
@media screen and (max-width: 480px) {
  .picture-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 25px;
    overflow: hidden;
    img {
      object-fit: cover;
      width: 100%;
    }
  }
  .design-container-mobile {
    display: flex;
    flex-direction: column;
    justify-content: start;
    padding: 0 3% 0 3%;
  }
  .design-container-desktop {
    display: none;
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
    border-radius: 25px;
    overflow: hidden;
    img {
      object-fit: cover;
      width: 100%;
    }
  }
  .design-container-mobile {
    display: flex;
    flex-direction: column;
    justify-content: start;
    padding: 0 3% 0 3%;
  }
  .design-container-desktop {
    display: none;
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
    border-radius: 50px;
    overflow: hidden;
    img {
      object-fit: cover;
      width: 100%;
    }
  }
  .design-container-desktop {
    display: flex;
    flex-direction: row;
    justify-content: start;
    padding: 0 3% 0 3%;
  }

  .design-container-mobile {
    display: none;
  }
  .text {
    display: flex;
    flex-direction: column;
    justify-content: start;
    padding: 3%;
    width: 80%;
  }

  .stack {
    color: var(--vt-c-white-soft);
  }
}
</style>
