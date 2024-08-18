<template>
  <div class="flex justify-end mb-4 space-x-4">
    <button 
      @click="$emit('add-task')" 
      class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600"
    >
      Add Task
    </button>
    <button 
      @click="$emit('clear-completed')" 
      class="bg-red-500 text-white px-4 py-2 rounded hover:bg-red-600"
    >
      Clear Completed
    </button>
  </div>
</template>
