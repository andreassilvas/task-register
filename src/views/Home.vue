<template>
  <div>
    <add-task v-if="showAddTask" @add-task="addTask" />
    <Tasks
      :tasks="tasks"
      @delete-task="handleDeleteTask"
      @toggle-reminder="toggleReminder"
    />
  </div>
  <Modal
    @close-modal="cancelDelete"
    :show-modal="showDeleteModal"
    :modalText="modalText"
    :buttonRText="cancelButton"
    :buttonLText="confirmButton"
    @confirm="confirmDelete()"
    @cancel="cancelDelete()"
  />
</template>
<script>
import Tasks from "../components/Tasks.vue";
import AddTask from "../components/AddTask.vue";
import Modal from "../components/ModalDialog.vue";

export default {
  components: { Tasks, AddTask, Modal },
  props: { showAddTask: Boolean },
  name: "Home",
  data() {
    return {
      tasks: [],
      taskToDelete: null,
      modalText: "Are you sure you want to remove the task?",
      confirmButton: "Yes, delete",
      cancelButton: "No",
      showDeleteModal: false,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    handleDeleteTask(id) {
      this.taskToDelete = id;
      this.showDeleteModal = true;
    },
    confirmDelete() {
      this.tasks = this.tasks.filter((item) => item.id !== this.taskToDelete);
      this.showDeleteModal = false;
      this.taskToDelete = null;
    },
    cancelDelete() {
      this.showDeleteModal = false;
      this.taskToDelete = null;
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((item) =>
        item.id === id ? { ...item, reminder: !item.reminder } : item
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March 5th at 2:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Food shopping",
        day: "March 7th at 2:00pm",
        reminder: false,
      },
      {
        id: 3,
        text: "Meeting with boss",
        day: "March 6th at 1:30pm",
        reminder: true,
      },
    ];
  },
};
</script>
