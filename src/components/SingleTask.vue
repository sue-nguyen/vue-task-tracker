<template>
  <div :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>
      {{ task.text }}
      <i
        @click="$emit('delete-task', task.id)"
        :class="[
          task.reminder
            ? 'fas fa-cancel-1 fa-times'
            : 'fas fa-cancel-2 fa-times',
        ]"
      ></i>
    </h3>
    <p>
      {{ task.day
      }}<i
        @click="$emit('toggle-reminder', task.id)"
        :class="[
          task.reminder
            ? 'fas fa-reminder-1 fa-bell'
            : 'fas fa-reminder-2 fa-bell',
        ]"
      ></i>
    </p>
  </div>
</template>

<script>
export default {
  name: 'SingleTask',
  props: {
    task: Object,
  },
};
</script>

<style scope>
.fas {
  cursor: pointer;
}

.fa-cancel-1 {
  color: white;
}

.fa-cancel-2 {
  color: red;
}

.fa-reminder-1 {
  color: white;
}

.fa-reminder-2 {
  color: navy;
}

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
}

.task.reminder {
  background: red;
  color: white;
}

.task h3,
.task p {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
