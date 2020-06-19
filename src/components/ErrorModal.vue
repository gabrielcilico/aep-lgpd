<template>
  <div class="modal">
    <MessageCard :message="message" />
    <div class="control">
      <button type="button" class="nes-btn is-error" @click="closeModal">OK</button>
    </div>
  </div>
</template>

<script>
import MessageCard from "@/components/MessageCard.vue";

export default {
  name: "ErrorModal",
  props: {
    message: {
      type: String,
      default: "Você precisa selecionar uma opção!"
    }
  },
  components: {
    MessageCard
  },
  data() {
    return {};
  },
  methods: {
    closeModal() {
      this.$emit("close");
    }
  }
};
</script>

<style>
.modal {
  position: absolute;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.9);
  z-index: 10;
}
.control {
  display: flex;
  flex-direction: row-reverse;
  width: 550px;
}
</style>
