<template>
  <div v-if="visible" class="modal">
    <div class="modal-content">
      <h3>{{ isEditMode ? 'Edit Task' : 'Add Task' }}</h3>
      <input v-model="taskTitle" placeholder="Task title" />
      <button @click="saveTask">{{ isEditMode ? 'Save' : 'Add' }}</button>
      <button @click="closeModal">Cancel</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    visible: Boolean,
    task: Object,
    isEditMode: Boolean,
  },
  data() {
    return {
      taskTitle: this.task ? this.task.title : '',
    };
  },
  methods: {
    saveTask() {
      const task = {
        id: this.task ? this.task.id : Date.now(),
        title: this.taskTitle,
        completed: this.task ? this.task.completed : false,
      };
      this.$emit('save-task', task);
    },
    closeModal() {
      this.$emit('close-modal');
    },
  },
  watch: {
    task(newTask) {
      this.taskTitle = newTask ? newTask.title : '';
    },
  },
};
</script>

<style scoped>
/* .modal { */
  /* I will style the modal here */
/* } */
</style>
