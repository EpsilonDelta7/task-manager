<template>
  <div class="container">
    <HeaderOne title="Task Manager" />
    <TasksList
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import HeaderOne from './components/HeaderOne.vue';
import TasksList from './components/TasksList.vue';
export default {
  name: 'App',
  components: {
    HeaderOne,
    TasksList,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    deleteTask(id) {
      if (confirm('Are sure you want to delete this task?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
      console.log(id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => {
        task.id === id ? { ...task, reminder: !task.reminder } : task;
      });
      console.log(id);
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Task 1',
        day: 'March 1st at 2:30 pm',
        reminder: true,
      },
    ];
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
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
</style>
