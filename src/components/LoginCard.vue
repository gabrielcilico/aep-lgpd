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
      name: "",
      dialog: false
    };
  },
  methods: {
    validate() {
      let name = this.name;
      if (!name || name.match(/[^A-Za-z0-9]/) || name.match(" ")) {
        this.returnErrorMessage();
        this.name = "";
        return;
      }
      this.$router.push(`/game/${name}`);
    },
    returnErrorMessage() {
      this.$emit("error");
    }
  }
};
</script>

<style scoped>
.card {
  width: 600px;
}
</style>
