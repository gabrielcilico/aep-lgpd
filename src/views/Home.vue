<template>
  <div class="container">
    <div class="nes-container is-rounded">
      <p>Salve rapaziada, teste da LGPD</p>
    </div>
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

.nes-container{
  color: black;
  background: aliceblue;
  

}
</style>
