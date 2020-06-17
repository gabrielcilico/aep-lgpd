<template>
  <header>
    <h1 class="nes-text is-primary">Quizz</h1>
    <router-link to="/about">Sobre</router-link>
  </header>
</template>

<script>
export default {
  name: 'Header',
};
</script>

<style>
header {
  background-color: red;
  display: flex;
  justify-content: space-between;
  padding: 15px 20px;
}
</style>
