<template>
  <div class="container">
    <transition appear @beforeEnter="illuBeforeEnter" @enter="illuEnter">
      <div class="left-pannel">
        <div class="illustration"></div>
      </div>
    </transition>
    <transition appear @beforeEnter="textContainerBeforeEnter" @enter="textContainerEnter">
      <div class="right-pannel">
        <div class="title-container">
          <img class="graphic" src="../assets/graphic1.svg" alt="Minimalist graphic design" />
          <h1>About me</h1>
        </div>
        <div class="animated-border">
          <div class="text-container">
            <transition appear @beforeEnter="textBeforeEnter" @enter="textEnter">
              <p>
                Hey, I'm Audrey DIEP ! <br />
                I'm a Web Developer and I wanted to create my website where I can share photos or
                projects that I'm proud of. The design of this website is inspired by the semester
                in Japan I spent in 2023. I'm so grateful for this unforgetable experience !
              </p>
            </transition>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import gsap from 'gsap'
export default {
  setup() {
    const illuBeforeEnter = (el) => {
      el.style.opacity = 0
      el.style.transform = 'translateY(60px)'
    }
    const illuEnter = (el) => {
      gsap.to(el, {
        opacity: 1,
        y: 0,
        duration: 2,
        ease: 'slow(0.7,0.7,false)'
      })
    }

    const textContainerBeforeEnter = (el) => {
      el.style.opacity = 0
      el.style.transform = 'translateX(60px)'
    }
    const textContainerEnter = (el) => {
      gsap.to(el, {
        opacity: 1,
        x: 0,
        duration: 2,
        ease: 'sine.inOut',
        delay: 0.2
      })
    }
    const textBeforeEnter = (el) => {
      el.style.opacity = 0
      el.style.transform = 'translatey(10px)'
    }

    const textEnter = (el) => {
      gsap.to(el, {
        opacity: 1,
        y: 0,
        duration: 1,
        ease: 'sine.inOut',
        delay: 0.4
      })
    }

    return {
      illuBeforeEnter,
      illuEnter,
      textContainerBeforeEnter,
      textContainerEnter,
      textBeforeEnter,
      textEnter
    }
  },
  data() {
    return {
      isLoading: false
    }
  },
  mounted() {
    setTimeout(() => {
      this.isLoading = true
    }, 1500)
  }
}
</script>

<style scoped>
@media screen and (max-width: 480px) {
  .container {
    display: flex;
    flex-direction: column;
  }
  .right-pannel {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .illustration {
    height: 100vw;
    margin: 5% 2% 5% 2%;
    background-color: var(--vt-c-white-soft);
    border-radius: 50% 50% 0 0;
    background-image: url('../assets/portrait.jpg');
    background-size: cover;
    background-position: bottom;
  }

  .graphic {
    width: 150px;
  }

  .title-container {
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .animated-border {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 0 50px 0 50px;
    overflow: hidden;
    padding: 2px;
  }

  .animated-border::before {
    content: '';
    display: block;
    background: linear-gradient(
      90deg,
      rgba(255, 255, 255, 0) 0%,
      rgba(102, 102, 102, 0.75) 50%,
      rgba(255, 255, 255, 0) 100%
    );
    transform: translate(0);
    height: 400px;
    width: 50px;
    position: absolute;
    animation: rotate 8s linear infinite;
    z-index: 0;
    top: 50%;
    transform-origin: top center;
  }

  .text-container {
    position: relative;
    z-index: 1;
    width: 100%;
    border-radius: 0 50px 0 50px;
    padding: 5%;
    color: var(--vt-c-white-soft);
    background-color: var(--vt-c-black);
  }
}

@media screen and (min-width: 481px) and (max-width: 1023px) {
  .illustration {
    height: 90vw;
    margin: 5% 2% 5% 2%;
    background-color: var(--vt-c-white-soft);
    border-radius: 50% 50% 0 0;
    background-image: url('../assets/portrait.jpg');
    background-size: cover;
    background-position: bottom;
  }

  .title-container {
    width: 100%;
    display: flex;
    justify-content: end;
  }

  .animated-border {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 0 50px 0 50px;
    overflow: hidden;
    padding: 2px;
  }

  .animated-border::before {
    content: '';
    display: block;
    background: linear-gradient(
      90deg,
      rgba(255, 255, 255, 0) 0%,
      rgba(102, 102, 102, 0.75) 50%,
      rgba(255, 255, 255, 0) 100%
    );
    transform: translate(0);
    height: 400px;
    width: 50px;
    position: absolute;
    animation: rotate 8s linear infinite;
    z-index: 0;
    top: 50%;
    transform-origin: top center;
  }

  .text-container {
    position: relative;
    z-index: 1;
    width: 100%;
    border-radius: 0 50px 0 50px;
    padding: 5%;
    color: var(--vt-c-white-soft);
    background-color: var(--vt-c-black);
  }
}

@media screen and (min-width: 1024px) {
  .left-pannel {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 5% 0 5% 0;
  }
  .illustration {
    height: 80vh;
    width: 100%;
    background-color: var(--vt-c-white-soft);
    border-radius: 50% 50% 0 0;
    background-image: url('../assets/portrait.jpg');
    background-size: cover;
    background-position: bottom;
  }
  .right-pannel {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 50px;
  }
  .container {
    display: grid;
    grid-gap: 5%;
    justify-content: center;
    grid-template-columns: 40% 40%;
    overflow: hidden;
  }
  .title-container {
    width: 99%;
    display: flex;
    justify-content: start;
  }

  .animated-border {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 0 50px 0 50px;
    overflow: hidden;
  }

  .animated-border::before {
    content: '';
    display: block;
    background: linear-gradient(
      90deg,
      rgba(255, 255, 255, 0) 0%,
      rgba(102, 102, 102, 0.75) 50%,
      rgba(255, 255, 255, 0) 100%
    );
    transform: translate(0);
    height: 400px;
    width: 100px;
    position: absolute;
    animation: rotate 8s linear infinite;
    z-index: 0;
    top: 50%;
    transform-origin: top center;
  }

  .text-container {
    position: relative;
    z-index: 1;
    width: 100%;
    margin: 2px;
    border-radius: 0 50px 0 50px;
    padding: 5%;
    color: var(--vt-c-black);
    background-color: var(--vt-c-white-soft);
    animation: inverse-gradient 0.5s ease;
  }

  .text-container:hover {
    color: var(--vt-c-white-soft);
    background-color: var(--vt-c-black);
    animation: gradient 0.5s ease;
    .redHover {
      color: var(--red);
      animation: text-gradient 1.5s ease;
    }
  }
  .graphic {
    width: 35%;
  }
}

@keyframes text-gradient {
  0% {
    color: var(--vt-c-black);
  }
  25% {
    color: var(--vt-c-white-soft);
  }
  100% {
    color: var(--red);
  }
}

@keyframes gradient {
  0% {
    background-color: var(--vt-c-white-soft);
    color: var(--vt-c-black);
  }
  100% {
    color: var(--vt-c-white-soft);
    background-color: var(--vt-c-black);
  }
}

@keyframes inverse-gradient {
  100% {
    background-color: var(--vt-c-white-soft);
    color: var(--vt-c-black);
  }
  0% {
    color: var(--vt-c-white-soft);
    background-color: var(--vt-c-black);
  }
}
</style>
