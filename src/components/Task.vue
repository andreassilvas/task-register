<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <i v-if="task.reminder" class="fa-regular fa-bell"></i>
    <div v-else class="icon-holder"></div>
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>
<script>
export default {
  name: "Task",
  props: { task: Object },
};
</script>
<style scoped>
.fas {
  color: red;
}

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.task.reminder {
  border-left: 5px solid #1f67e7;
}
.fa-bell:before {
  color: #1f67e7;
}
.icon-holder {
  height: 25px;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
