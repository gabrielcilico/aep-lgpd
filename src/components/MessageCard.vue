<template>
  <section class="card">
    <i class="nes-bcrikko"></i>
    <p class="nes-balloon from-left nes-pointer">
      {{ message }}
    </p>
  </section>
</template>

<script>
export default {
  name: "MessageCard",
  props: {
    message: {
      type: String,
      default: "Seja bem vindo! Escolha um nome e comece a jogar!"
    }
  }
};
</script>

<style scoped>
.card {
  width: 600px;
  display: flex;
  align-items: flex-end;
}
.card p {
  max-width: 80%;
}
.card i {
  bottom: -45px;
}
</style>
