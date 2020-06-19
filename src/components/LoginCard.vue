<template>
  <div class="nes-container is-dark with-title is-centered card">
    <h1 class="title">Começar</h1>
    <div class="nes-field">
      <label for="name_field">Seu nome</label>
      <input
        type="text"
        id="name_field"
        class="nes-input"
        v-model="name"
        @keyup.enter="validate"
        autocomplete="off"
      />
    </div>
    <button type="button" class="nes-btn is-warning" @click="validate">Começar</button>
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
      if (
        !name ||
        name.match(/[^A-Za-z0-9]/) ||
        name.match(" ") ||
        name.length < 3 ||
        name.length > 12
      ) {
        this.returnErrorMessage();
        this.name = "";
        return;
      }
      this.$store.state.player = name;
      this.$router.push("/game");
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
button {
  margin-top: 10px;
}
</style>
