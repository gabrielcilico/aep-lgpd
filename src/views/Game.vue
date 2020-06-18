<template>
  <div class="content">
    <div class="container" v-if="openMessage">
      <MessageCard :message="message" />
    </div>
    <div class="container">
      <QuestionCard
        :questionNumber="currentQuestion.number"
        :question="currentQuestion.question"
        :answers="currentQuestion.answers"
        @answer="getAnswer"
      />
    </div>
  </div>
</template>

<script>
import QuestionCard from "@/components/QuestionCard.vue";
import MessageCard from "@/components/MessageCard.vue";

export default {
  name: "Game",
  components: {
    QuestionCard,
    MessageCard
  },
  data() {
    return {
      message: "",
      isCorrect: true,
      openMessage: false,
      currentQuestion: {
        number: 6,
        question:
          "Mussum Ipsum, cacilds vidis litro abertis. Viva Forevis aptent taciti sociosqu ad litora torquent. Atirei o pau no gatis, per gatis num morreus. Vehicula non. Ut sed ex eros. Vivamus sit amet nibh non tellus tristique interdum. Copo furadis é disculpa de bebadis, arcu quam euismod magna.",
        answers: [
          {
            id: 1,
            title: "Resposta 1"
          },
          {
            id: 2,
            title: "Resposta 2"
          },
          {
            id: 3,
            title: "Resposta 3"
          },
          {
            id: 4,
            title: "Resposta 4"
          }
        ],
        idCorrectAnswer: 1
      }
    };
  },
  methods: {
    getAnswer(value) {
      this.isCorrect = this.currentQuestion.idCorrectAnswer == value;
      if (this.isCorrect) {
        this.message = "Parabéns! Você acertou!";
      } else {
        let answer = this.currentQuestion.answers.filter(
          answer => answer.id == this.currentQuestion.idCorrectAnswer
        )[0];
        this.message =
          "Oops! Você Errou! Na verdade a resposta correta é '" + answer.title + "'...";
      }
    }
  },
  watch: {
    message() {
      console.log("entrou");
      this.openMessage = true;
      setTimeout(() => {
        this.openMessage = false;
      }, 15000);
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
