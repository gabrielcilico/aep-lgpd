<template>
  <div class="structure">
    <ErrorModal v-if="hasError" @close="hasError = false" />
    <ErrorModal v-if="hasTip" :message="tip" @close="hasTip = false" />
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
      <div class="actions">
        <button class="nes-btn tip" v-if="$store.state.tips > 0" @click="showTip">Dica</button>
        <button type="button" class="nes-btn is-warning" @click="confirmAnswer">Confirmar</button>
      </div>
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
    answers: Array,
    tip: String
  },
  data() {
    return {
      choosenAnswer: 0,
      hasError: false,
      hasTip: false
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
    },
    showTip() {
      if (this.$store.state.tips <= 0) {
        this.hasTip = false;
        return;
      }
      this.$store.state.tips--;
      this.hasTip = true;
    }
  }
};
</script>

<style scoped>
.structure {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.tip {
  margin-right: 10px;
}
.card {
  max-width: 90vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.controller-group {
  width: 90vw;
  display: flex;
  flex-flow: row wrap;
  color: white;
  justify-content: space-between;
  align-content: center;
  margin-top: 15px;
}
.progress-info {
  max-width: 85vw;
  display: flex;
  align-items: center;
  justify-content: center;
}
.progress-info h3 {
  padding: 5px 10px;
  margin-right: 10px;
}
.answer-radio {
  border-top: 2px solid #fff !important;
  padding-top: 10px;
  width: 80%;
}
</style>
