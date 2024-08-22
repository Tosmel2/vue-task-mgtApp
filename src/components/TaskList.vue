<template>
  <div>
    <input v-model="searchQuery" 
    placeholder="Search tasks"
    class="w-full p-2 mb-4 border border-gray-300 rounded"
     />
    <ul class="p-3 rounded shadow bg-slate-200">
      <task-item 
        v-for="task in filteredTasks" 
        :key="task.id" 
        :task="task"
        @edit="editTask"
        @delete="deleteTask"
        @toggle-complete="toggleComplete"
      />
    </ul>
  </div>
</template>

<script>
import TaskItem from './TaskItem.vue';

export default {
  components: { TaskItem },
  data() {
    return {
      searchQuery: '',
    };
  },
  props: {
    tasks: Array,
  },
  computed: {
    filteredTasks() {
      return this.tasks.filter(task =>
        task.title.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
  methods: {
    editTask(task) {
      this.$emit('edit-task', task);
    },
    deleteTask(task) {
      this.$emit('delete-task', task);
    },
    toggleComplete(task) {
      this.$emit('toggle-complete', task);
    },
  },
};
</script>
