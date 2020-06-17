<template>
  <header>
    <h1 class="nes-text is-primary">Quiz LGPD</h1>
    <nav>
      <router-link class="nes-btn" to="/game">Recomeçar</router-link>
      <router-link class="nes-btn" to="/">Desistir</router-link>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style>
header {
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: space-between;
  padding: 15px 20px;
}
nav {
  justify-content: space-between;
}
</style>
