<template>
  <div class="container">
    <HeaderTab
      @toggle-add-task="toggleAddTask"
      title="Task Tracker"
      :showAddTask="showAddTask"
    />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <TaskArray
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import HeaderTab from './components/HeaderTab';
import TaskArray from './components/TaskArray';
import AddTask from './components/AddTask';

export default {
  name: 'App',
  components: {
    HeaderTab,
    TaskArray,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: true,
    };
  },
  methods: {
    deleteTask(id) {
      if (confirm('Are you sure you want to delete this task?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Tilt+Neon');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Tilt Neon', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 5px solid darkslateblue;
  padding: 30px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}

.btn-block:hover {
  box-shadow: 2px 2px 3px grey;
}
</style>
