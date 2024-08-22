<template>
  <div v-if="visible" class="fixed inset-0 z-10 flex items-center justify-center w-screen overflow-y-auto modal">
    <div class="modal-content absolute w-[80%] md:w-[35%] rounded shadow bg-white min-h-48 p-2">
      <div class="flex flex-col items-center">
        <h3>{{ isEditMode ? 'Edit Task' : 'Add Task' }}</h3>
        <textarea v-model="taskTitle" placeholder="Add Task" class="rounded w-[90%] my-1 p-2 bg-gray-200" />
      <div class="flex my-2">
        <button class="px-4 py-2 mr-2 text-white rounded bg-sky-500 hover:border-sky-600" @click="saveTask">{{ isEditMode ? 'Save' : 'Add' }}</button>
      <button class="px-4 py-2 text-white bg-orange-500 rounded hover:border-orange-500" @click="closeModal">Cancel</button>
      </div>
      </div>
      
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
