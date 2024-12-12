<template>
  <nav class="nav-container">
    <div class="nav-bar">
      <RouterLink to="/" class="nav-link">About</RouterLink>
      <RouterLink to="/projects" class="nav-link">Web</RouterLink>
      <RouterLink to="/" class="nav-link"
        ><img class="logo" src="../assets/logo.svg" alt="Minimalist sun design"
      /></RouterLink>
      <RouterLink to="/design" class="nav-link">Design</RouterLink>
      <RouterLink to="/gallery" class="nav-link">Gallery</RouterLink>
    </div>
  </nav>
</template>

<script></script>

<style scoped>
@media screen and (max-width: 480px) {
  .logo {
    margin-top: 10px;
    width: 25vw;
  }
  .nav-bar {
    padding: 10px 20px 10px 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    animation: opacity 3s ease;
    font-size: 16px;
  }
  .nav-container {
    height: 7vh;
    background-color: var(--vt-c-black);
    border-radius: 0 0 25px 25px;
    border-bottom: solid 1px rgba(129, 129, 129, 0.5);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: sticky;
    top: 0;
    z-index: 10;
  }
}
@media screen and (min-width: 481px) and (max-width: 1023px) {
  .logo {
    margin-top: 10px;
    width: 15vw;
  }
  .nav-bar {
    padding-top: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    animation: opacity 3s ease;
    font-size: 20px;
  }
  .nav-container {
    height: 7vh;
    background-color: var(--vt-c-black);
    border-radius: 0 0 50px 50px;
    border-bottom: solid 1px rgba(129, 129, 129, 0.5);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: sticky;
    top: 0;
    z-index: 10;
  }
}
@media screen and (min-width: 1024px) {
  .logo {
    margin-top: 10px;
    width: 5vw;
  }
  .nav-bar {
    display: flex;
    justify-content: center;
    align-items: center;
    animation: opacity 3s ease;
    img {
      margin-top: 8px;
    }
  }
  .nav-container {
    height: 7vh;
    background-color: var(--vt-c-black);
    border-radius: 0 0 50px 50px;
    border-bottom: solid 2px rgba(129, 129, 129, 0.5);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: sticky;
    top: 0;
    z-index: 10;
  }

  .nav-container:hover {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    transition: 0.5s;
    border-bottom: solid 2px var(--vt-c-text-dark-2);
  }
}
</style>
