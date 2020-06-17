<template>
  <div class="nes-container is-dark with-title is-centered card">
    <h1 class="title">Pergunta #{{ questionNumber }}</h1>
    <p class="nes-text is-error">{{ question }}</p>

    <div v-for="answer in answers" :key="answer.id">
      <label>
        <input type="radio" class="nes-radio" name="answer" checked />
        <span>{{ answer.title }}</span>
      </label>
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
        }
      ]
    }
  }
};
</script>

<style>
.card {
  max-width: 600px;
}
</style>
