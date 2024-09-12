<template>
  <form @submit.prevent="onSubmit" class="add-form">
    <div class="form-control">
      <label for="inputTask">Task</label>
      <input
        id="inputTask"
        type="text"
        v-model="text"
        name="text"
        placeholder="Add Task"
      />
    </div>
    <div class="form-control">
      <label for="inputDay">Day & Time</label>
      <input
        id="inputDay"
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label for="inputReminder">Set Reminder</label>
      <input
        id="inputReminder"
        type="checkbox"
        v-model="reminder"
        name="reminder"
      />
    </div>
    <Modal
      :show-modal="showModal"
      :modalText="modalText"
      @close-modal="showModal = false"
      :showRightButtom="false"
      :buttonLText="buttonRText"
    />
    <input type="submit" value="Save Task" class="button btn-block" />
  </form>
</template>

<script>
import Modal from "./ModalDialog.vue";
export default {
  components: { Modal },
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
      showModal: false,
      modalText: "Task fields cannot be empty.",
      buttonRText: "Close",
    };
  },
  methods: {
    onSubmit() {
      if (this.text.length === 0) {
        this.showModal = true;
        return;
      }
      const newTask = {
        id: Math.floor(Math.random() * 10000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };
      console.log(newTask);
      this.$emit("add-task", newTask);
      this.text = "";
      this.day = "";
      this.reminder = false;
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
