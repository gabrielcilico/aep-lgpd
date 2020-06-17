<template>
  <div class="container">
    <LoginCard />
  </div>
</template>

<script>
import LoginCard from "@/components/LoginCard.vue";

export default {
  name: "Home",
  components: {
    LoginCard
  }
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-content: center;
  padding: 30px;
}
</style>
