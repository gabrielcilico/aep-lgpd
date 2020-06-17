<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";

export default {
  name: "Home",
  components: {
    Header
  }
};
</script>

<style>
*,
body {
  padding: 0;
  margin: 0;
  font-family: "Press Start 2P", cursive;
}
body {
  background-image: url("assets/img/background.png");
}
</style>
