<template>
  <div class="content">
    <div class="container">
      <MessageCard :message="message" />
    </div>
    <div class="container">
      <LoginCard />
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
      message: "Seja bem vindo! Escolha um nome e comece a jogar!"
    };
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
