<template>
  <div class="container">
    <div class="left-pannel">
      <div class="illustration"></div>
    </div>
    <div class="right-pannel">
      <div class="title-container">
        <img class="graphic" src="../assets/graphic1.svg" alt="Minimalist graphic design" />
        <h1>About me</h1>
      </div>
      <div class="text-container">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla maximus laoreet odio id
          lacinia. Quisque felis felis, ultrices et massa id, sollicitudin rutrum sem. Donec
          interdum tristique condimentum. Sed elementum mi sit amet neque consectetur eleifend. Sed
          gravida enim non massa tincidunt, at imperdiet justo lobortis. Proin luctus magna in
          gravida euismod. Etiam eu turpis vitae risus fermentum lacinia vitae ac mauris. Proin
          congue at neque vitae rutrum. Vivamus vehicula mauris id laoreet finibus. Integer commodo
          tempus vestibulum. Morbi consequat tincidunt justo eget scelerisque. Curabitur ante risus,
          sodales ac dapibus sed, finibus non turpis. Vivamus vulputate odio id semper tincidunt.
          Vestibulum velit purus, congue id leo non, pellentesque semper magna. Cras sed vestibulum
          justo, eu condimentum sapien.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.left-pannel {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 50px;
}
.illustration {
  height: 700px;
  width: 40vw;
  background-color: var(--vt-c-white-soft);
  border-radius: 50% 50% 0 0;
  background-image: url('../assets/portrait.jpg');
  background-size: cover;
}
.right-pannel {
  display: flex;
  flex-direction: column;
  justify-content: end;
  align-items: center;
  padding: 50px;
}
.container {
  display: grid;
  grid-gap: 5%;
  justify-content: center;
  grid-template-columns: 40% 40%;
}
.title-container {
  width: 100%;
  display: flex;
  justify-content: start;
}

.text-container {
  border-radius: 0 50px 0 50px;
  padding: 5%;
  color: var(--vt-c-black);
  background-color: var(--vt-c-white-soft);
}

.graphic {
  width: 35%;
}
</style>
