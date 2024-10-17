<script>
export default {
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },
  unmounted() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      console.log('scroll')
      this.$router.push('/gallery')
    }
  }
}
</script>

<template>
  <RouterView />
</template>

<style scoped>
.view {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
