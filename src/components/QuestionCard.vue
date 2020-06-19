<template>
  <div>
    <ErrorModal v-if="hasError" @close="hasError = false" />
    <div class="nes-container is-dark with-title is-centered card">
      <h1 class="title">Pergunta #{{ questionNumber }}</h1>
      <p class="nes-text is-error">{{ question }}</p>

      <div v-for="answer in answers" :key="answer.id" class="answer-radio">
        <label>
          <input
            type="radio"
            v-model="choosenAnswer"
            :value="answer.id"
            class="nes-radio"
            name="answer"
          />
          <span>{{ answer.title }}</span>
        </label>
      </div>
    </div>
    <div class="controller-group">
      <div class="progress-group">
        <progress class="nes-progress is-warning" :value="questionNumber * 10" max="100"></progress>
        <div class="progress-info">
          <h3 class="nes-text is-warning">Progresso:</h3>
          <div class="nes-badge is-splited">
            <span class="is-warning">{{ questionNumber }}</span>
            <span class="is-dark">10</span>
          </div>
        </div>
      </div>
      <button type="button" class="nes-btn is-warning" @click="confirmAnswer">Confirmar</button>
    </div>
  </div>
</template>

<script>
import ErrorModal from "@/components/ErrorModal.vue";

export default {
  name: "QuestionCard",
  components: {
    ErrorModal
  },
  props: {
    questionNumber: Number,
    question: String,
    answers: Array
  },
  data() {
    return {
      choosenAnswer: 0,
      hasError: false
    };
  },
  methods: {
    confirmAnswer() {
      this.hasError = false;
      let value = this.choosenAnswer;
      if (!value) {
        this.hasError = true;
        return;
      }
      this.$emit("answer", value);
    }
  }
};
</script>

<style scoped>
.card {
  min-width: 600px;
  max-width: 1280px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.controller-group {
  display: flex;
  justify-content: space-between;
  color: white;
  align-items: start;
  margin-top: 15px;
}
.progress-group {
  width: 60%;
}
.progress-info {
  display: flex;
  align-items: center;
}
.progress-info h3 {
  background-color: #212529;
  padding: 5px 10px;
  margin-right: 10px;
}
.answer-radio {
  border-top: 2px solid #fff !important;
  padding-top: 10px;
  width: 80%;
}
</style>