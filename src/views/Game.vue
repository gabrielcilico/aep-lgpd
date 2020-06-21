<template>
  <div class="content">
    <div class="container badges">
      <div class="nes-badge is-splited badge">
        <span class="is-dark">ACERTOS</span>
        <span class="is-warning">{{ hits }}</span>
      </div>
      <div class="nes-badge is-splited tips">
        <span class="is-dark">DICAS</span>
        <span class="is-warning">{{ $store.state.tips }}</span>
      </div>
    </div>
    <div class="container" v-if="openMessage">
      <div class="content">
        <MessageCard :message="message" :key="cardKey" />
        <div class="options">
          <progress class="nes-progress is-primary" :value="progress" :key="progress" max="100"></progress>
          <button type="button" class="nes-btn is-primary" @click="pressContinue">Continuar</button>
        </div>
      </div>
    </div>
    <div class="container" v-else>
      <QuestionCard
        :questionNumber="currentQuestion.number"
        :question="currentQuestion.question"
        :answers="currentQuestion.answers"
        :tip="currentQuestion.tip"
        @answer="getAnswer"
        v-if="currentNumberQuestion <= 10"
      />
    </div>
  </div>
</template>

<script>
import QuestionCard from "@/components/QuestionCard.vue";
import MessageCard from "@/components/MessageCard.vue";
import dataQuestions from "@/assets/questions.json";

export default {
  name: "Game",
  components: {
    QuestionCard,
    MessageCard
  },
  data() {
    return {
      message: "",
      hits: 0,
      openMessage: false,
      progress: 100,
      cardKey: 1,
      player: this.$store.state.player,
      questions: dataQuestions,
      currentQuestion: {},
      currentNumberQuestion: 0
    };
  },
  methods: {
    getAnswer(value) {
      let message = "";
      if (this.currentQuestion.idCorrectAnswer == value) {
        message = `Parabéns, ${this.player}! Você acertou!`;
        this.hits++;
      } else {
        let answer = this.currentQuestion.answers.filter(
          answer => answer.id == this.currentQuestion.idCorrectAnswer
        )[0];
        message =
          `Oops, ${this.player}! Você Errou! Na verdade a resposta correta é '` +
          answer.title +
          "'...";
      }
      this.openTheMessage(message);
    },
    nextQuestion() {
      if (this.currentNumberQuestion >= 10) {
        this.$router.push("/finish");
        return;
      }
      this.cardKey++;
      if (this.openMessage) {
        this.updateQuestion();
        this.openMessage = false;
      }
    },
    updateQuestion() {
      if (this.questions.length > this.currentNumberQuestion) {
        this.currentQuestion = this.questions[this.currentNumberQuestion];
        this.currentQuestion.answers = this.currentQuestion.answers.sort(
          () => 0.5 - Math.random()
        );
      }
      this.currentNumberQuestion++;
    },
    openTheMessage(value) {
      this.message = value;
      this.openMessage = true;
      this.timerControl();
    },
    timerControl() {
      this.progress = 100;
      let timer = setInterval(() => {
        this.progress -= 5;
        if (this.progress <= 0 || !this.openMessage) {
          this.nextQuestion();
          clearInterval(timer);
        }
      }, 1000);
    },
    pressContinue() {
      this.progress = 0;
    }
  },
  mounted() {
    if (!this.$store.state.player) {
      this.$router.push("/");
    }
    this.$store.state.tips = 3;
    this.updateQuestion();
  },
  watch: {
    hits() {
      this.$store.state.hits = this.hits;
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
  width: 100%;
  justify-content: center;
  align-content: center;
  padding: 30px;
}
.options {
  display: flex;
  justify-content: space-between;
  margin-top: 75px;
  align-content: center;
}
.options progress {
  max-width: 60%;
}
.badges {
  display: flex;
  justify-content: center;
  flex-flow: row wrap;
}
.badge {
  width: 15em !important;
}
.tips {
  margin-left: 20px;
}
</style>
