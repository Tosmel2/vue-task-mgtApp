<template>
  <div class="flex justify-center mb-4 space-x-4 md:justify-end">
    <button 
      @click="$emit('add-task')" 
      class="px-4 py-2 text-white rounded bg-sky-500 hover:bg-blue-600"
    >
      Add Task
    </button>
    <button 
      @click="$emit('clear-completed')" 
      class="px-4 py-2 text-white bg-orange-500 rounded hover:bg-red-600"
    >
      Clear Completed
    </button>
  </div>
</template>
