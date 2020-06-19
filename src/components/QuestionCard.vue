<template>
  <div>
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
      <progress class="nes-progress is-warning" :value="questionNumber * 10" max="100"></progress>
      <div class="nes-badge is-splited">
        <span class="is-warning">{{ questionNumber }}</span>
        <span class="is-dark">10</span>
      </div>
      <button type="button" class="nes-btn is-warning" @click="confirmAnswer">Confirmar</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "QuestionCard",
  props: {
    questionNumber: Number,
    question: String,
    answers: Array
  },
  data() {
    return {
      choosenAnswer: 1
    };
  },
  methods: {
    buttonController() {},
    confirmAnswer() {
      let value = this.choosenAnswer;
      if (!value) {
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
  align-items: center;
  margin-top: 20px;
}
.controller-group progress {
  max-width: 40%;
}
.answer-radio {
  border-top: 2px solid #fff !important;
  padding-top: 10px;
  width: 80%;
}
</style>
