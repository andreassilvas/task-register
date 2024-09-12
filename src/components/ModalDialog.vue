<template>
  <div v-if="showModal" class="modal-overlay" @click="$emit('close-modal')">
    <div class="modal-dialog">
      <p>{{ modalText }}</p>
      <Button
        v-if="showLeftButtom"
        bc="#BE4144"
        color="#BE4144"
        :text="buttonLText"
        @button-click="$emit('confirm')"
      />

      <Button
        v-if="showRightButtom"
        @button-click="$emit('cancel')"
        :text="buttonRText"
      />
    </div>
  </div>
</template>
<script>
import Button from "./Button.vue";
export default {
  components: { Button },
  props: {
    showModal: Boolean,
    modalText: String,
    showRightButtom: { type: Boolean, default: true },
    showLeftButtom: { type: Boolean, default: true },
    buttonRText: String,
    buttonLText: String,
  },
  emits: ["confirm", "cancel", "close-modal"],
};
</script>
<style scoped>
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
}
.modal-dialog {
  padding: 35px;
  height: 200px;
  background: white;
  border-radius: 15px;
  text-align: center;
}
p {
  margin: 20px;
}
.buttons {
  margin: 10px;
}
</style>
