<template>
  <div>
    <div class="container">
      <QuestionCard
        :questionNumber="question.number"
        :question="question.question"
        :answers="question.answers"
      />
    </div>
  </div>
</template>

<script>
import QuestionCard from "@/components/QuestionCard.vue";

export default {
  name: "Game",
  components: {
    QuestionCard
  },
  data() {
    return {
      question: {
        number: 1,
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
        ]
      }
    };
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
