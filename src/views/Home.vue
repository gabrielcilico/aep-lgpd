<template>
  <div class="content">
    <div class="container">
      <MessageCard :message="message" :key="messageKey" />
    </div>
    <div class="container">
      <LoginCard @error="nameError" />
    </div>
  </div>
</template>

<script>
import LoginCard from "@/components/LoginCard.vue";
import MessageCard from "@/components/MessageCard.vue";

export default {
  name: "Home",
  components: {
    LoginCard,
    MessageCard
  },
  data() {
    return {
      message: "Seja bem vindo! Escolha um nome e comece a jogar!",
      messageKey: 1
    };
  },
  methods: {
    nameError() {
      this.message = "";
      this.message =
        "Este nome não é válido! Tente usar um nome sem caracteres especiais e sem espaços.";
      this.messageKey++;
    }
  }
};
</script>

<style scoped>
.content {
  display: flex;
  flex-direction: column;
}
.container {
  display: flex;
  justify-content: center;
  align-content: center;
  padding: 30px;
}
</style>
