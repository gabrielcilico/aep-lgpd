<template>
  <div class="content">
    <div class="container">
      <div class="nes-container is-dark with-title card">
        <p class="title">JOGO FINALIZADO!</p>
        <p>
          Muito obrigado por jogar,
          <span :class="classPoints" class="nes-text">{{ player }}</span>!
        </p>
        <p :class="classPoints" class="nes-text">{{ message }}</p>
        <p>Tire um print desta tela e desafie seus amigos a superar sua pontuação!</p>
        <router-link class="nes-btn" to="/">Jogar novamente</router-link>
      </div>
    </div>
    <div class="container">
      <div class="nes-badge">
        <span :class="classPoints">
          <h2>{{ hits }}</h2>
          <p>PONTOS!</p>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Finish",
  data() {
    return {
      player: "",
      classPoints: "is-primary",
      hits: 0,
      message: "",
      messages: [
        "Você teve um desempenho de principiante, jogue novamente!",
        "Você pode melhorar... jogue novamente!",
        "Você está acima da média, mas ainda há o que aprender!",
        "Muito bem, você é quase um gênio!",
        "Incrível, você quase gabaritou!",
        "Você é o mestre supremo do universo LGPD, perfeito!"
      ]
    };
  },
  methods: {
    checkPerformance() {
      let hits = this.hits;
      let messages = this.messages;
      if (hits < 3) {
        this.setClassPoints("is-error");
        this.setMessage(messages[0]);
        return;
      }
      if (hits < 5) {
        this.setClassPoints("is-error");
        this.setMessage(messages[1]);
        return;
      }
      if (hits < 7) {
        this.setClassPoints("is-warning");
        this.setMessage(messages[2]);
        return;
      }
      if (hits < 9) {
        this.setClassPoints("is-primary");
        this.setMessage(messages[3]);
        return;
      }
      if (hits < 10) {
        this.setClassPoints("is-primary");
        this.setMessage(messages[4]);
        return;
      }
      this.setClassPoints("is-success");
      this.setMessage(messages[5]);
    },
    setClassPoints(value) {
      this.classPoints = value;
    },
    setMessage(message) {
      this.message = message;
    }
  },
  mounted() {
    if (!this.$store.state.player) {
      this.$router.push("/");
    }
    this.player = this.$store.state.player;
    this.hits = this.$store.state.hits;
    this.checkPerformance();
  }
};
</script>

<style>
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
.card {
  width: 100%;
  max-width: 720px;
}
button {
  margin-top: 25px;
}
</style>
