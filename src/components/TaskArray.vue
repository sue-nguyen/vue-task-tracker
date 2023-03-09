<template>
  <div :key="task.id" v-for="task in tasks">
    <SingleTask
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import SingleTask from './SingleTask';

export default {
  name: 'TaskArray',
  props: {
    tasks: Array,
  },
  components: {
    SingleTask,
  },
  emits: ['delete-task', 'toggle-reminder'],
};
</script>

<style></style>
