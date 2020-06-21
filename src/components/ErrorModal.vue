<template>
  <div class="modal">
    <div class="baloon">
      <MessageCard :message="message" style="width: 100%" />
      <div class="control">
        <button type="button" class="nes-btn is-error" @click="closeModal">OK</button>
      </div>
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
  methods: {
    closeModal() {
      this.$emit("close");
    }
  }
};
</script>

<style>
.modal {
  position: fixed;
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
.baloon {
  max-width: 95vw;
  display: flex;
  flex-direction: column;
}
.control {
  display: flex;
  flex-direction: row-reverse;
  margin-right: 35px;
}
</style>
