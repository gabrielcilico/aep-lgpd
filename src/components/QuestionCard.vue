<template>
  <div>
    <div class="nes-container is-dark with-title is-centered card">
      <h1 class="title">Pergunta #{{ questionNumber }}</h1>
      <p class="nes-text is-error">{{ question }}</p>

      <div v-for="answer in answers" :key="answer.id">
        <label>
          <input type="radio" :id="answer.id" class="nes-radio" name="answer" />
          <span>{{ answer.title }}</span>
        </label>
      </div>
    </div>
    <div class="controller-group">
      <progress class="nes-progress is-small" :value="questionNumber * 10" max="100"></progress>
      <div class="nes-badge is-splited">
        <span class="is-primary">{{ questionNumber }}</span>
        <span class="is-dark">10</span>
      </div>
      <button type="button" class="nes-btn is-success" id="confirm">Confirmar</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "QuestionCard",
  props: {
    questionNumber: Number,
    question: String,
    answers: {
      type: Array,
      default: [
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
        },
        {
          id: 5,
          title: "Resposta 5"
        }
      ]
    }
  },
  methods: {
    buttonController() {},
    answerController() {
      let valor = document.querySelector('input[name="answer"]:checked').value;
      console.log(valor);
    }
  },
  mounted() {}
};
</script>

<style scoped>
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
</style>
