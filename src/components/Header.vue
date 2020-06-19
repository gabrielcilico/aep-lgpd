<template>
  <header>
    <h1 class="nes-text is-warning">Quiz LGPD</h1>
    <nav>
      <router-link class="nes-btn" to="/" v-if="$store.state.player">Desistir</router-link>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      player: this.$store.state.player
    };
  }
};
</script>

<style>
header {
  display: flex;
  justify-content: space-between;
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 1), rgba(0, 0, 0, 0.1));
  padding: 15px 20px;
}
</style>
