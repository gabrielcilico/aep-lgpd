<template>
  <div class="nes-container is-dark with-title is-centered card">
    <h1 class="title">Começar</h1>
    <div class="nes-field">
      <label for="name_field">Seu nome</label>
      <input type="text" id="name_field" class="nes-input" v-model="name" />
    </div>
    <button type="button" class="nes-btn is-success" @click="validate">Começar</button>
  </div>
</template>

<script>
export default {
  name: "LoginCard",
  data() {
    return {
      name: ""
    };
  },
  methods: {
    validate() {
      this.$router.push("/game/");
    }
  }
};
</script>

<style>
.card {
  max-width: 600px;
}
</style>
