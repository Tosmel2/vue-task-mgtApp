<template>
   <div class="min-h-screen bg-gray-100 min-w-full p-8">
    <h1 class="text-3xl font-bold text-center text-blue-600 mb-8">Task Manager</h1>
    <task-actions 
      @add-task="showAddTaskModal"
      @clear-completed="clearCompletedTasks"
    />
    <task-list 
      :tasks="tasks"
      @edit-task="showEditTaskModal"
      @delete-task="deleteTask"
      @toggle-complete="toggleComplete"
    />
    <task-modal 
      v-if="isModalVisible"
      :visible="isModalVisible"
      :task="currentTask"
      :isEditMode="isEditMode"
      @save-task="saveTask"
      @close-modal="closeModal"
    />
  </div>
</template>

<script>
import TaskList from '@/components/TaskList.vue';
import TaskActions from '@/components/TaskActions.vue';
import TaskModal from '@/components/TaskModal.vue';

export default {
  components: {
    TaskList,
    TaskActions,
    TaskModal,
  },
  data() {
    return {
      tasks: JSON.parse(localStorage.getItem('tasks')) || [],
      isModalVisible: false,
      currentTask: null,
      isEditMode: false,
    };
  },
  methods: {
    showAddTaskModal() {
      this.isEditMode = false;
      this.currentTask = null;
      this.isModalVisible = true;
    },
    showEditTaskModal(task) {
      this.isEditMode = true;
      this.currentTask = task;
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
    saveTask(task) {
      if (this.isEditMode) {
        const index = this.tasks.findIndex(t => t.id === task.id);
        this.$set(this.tasks, index, task);
      } else {
        this.tasks.push(task);
      }
      this.updateLocalStorage();
      this.closeModal();
    },
    deleteTask(task) {
      this.tasks = this.tasks.filter(t => t.id !== task.id);
      this.updateLocalStorage();
    },
    toggleComplete(task) {
      task.completed = !task.completed;
      this.updateLocalStorage();
    },
    clearCompletedTasks() {
      this.tasks = this.tasks.filter(t => !t.completed);
      this.updateLocalStorage();
    },
    updateLocalStorage() {
      localStorage.setItem('tasks', JSON.stringify(this.tasks));
    },
  },
};
</script>
