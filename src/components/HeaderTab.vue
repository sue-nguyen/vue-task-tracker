<template>
  <header>
    <h1>{{ title }}</h1>
    <AddButton
      @btn-click="$emit('toggle-add-task')"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? 'red' : 'green'"
    />
  </header>
  <div>
    <p>
      Click the <i class="fas fa-bell"></i> right next to the task you want to prioritize.
      <br />
      The <span style="color: green">Add Task</span> form can be open and closed on click.
    </p>
  </div>
</template>

<script>
import AddButton from './AddButton';

export default {
  name: 'HeaderTab',
  props: {
    title: String,
    showAddTask: Boolean,
  },
  components: {
    AddButton,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  color: darkslateblue;
}
.fas {
  color: navy;
}
</style>
