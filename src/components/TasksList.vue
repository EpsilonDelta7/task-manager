<template>
  <div v-for="task in tasks" :key="task.id">
    <TaskItem
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import TaskItem from './TaskItem.vue';
export default {
  name: 'TasksList',
  props: {
    tasks: Array,
  },
  components: {
    TaskItem,
  },
  emits: [
    {
      'toggle-reminder': (id) => {
        if (typeof id === 'number') {
          return true;
        } else {
          console.warn(
            `ID is incorrect type of ${typeof id}. Expected number.`
          );
          return false;
        }
      },
      'delete-task': (id) => {
        if (typeof id === 'number') {
          return true;
        } else {
          console.warn(
            `ID is incorrect type of ${typeof id}. Expected number.`
          );
          return false;
        }
      },
    },
  ],
};
</script>
