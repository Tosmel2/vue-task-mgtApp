<template>
  <li :class="{ completed: task.completed }" class="justify-between gap-4 py-3 mb-4 border-b border-gray-300 md:flex md:items-center">
    <div @click="$emit('toggle-complete', task)" class="mb-3 md:mb-0">{{ task.title }}</div>
    <div class="flex gap-2">
      <button class="p-2 text-white bg-blue-500 rounded" @click="$emit('edit', task)">Edit</button>
      <button class="p-2 text-white bg-red-500 rounded" @click="$emit('delete', task)">Delete</button>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    task: Object,
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>

<!-- 
<template>
  <li 
    :class="['flex justify-between items-center p-4 mb-2 rounded shadow', task.completed ? 'bg-green-100 line-through' : 'bg-white']"
  >
    <span 
      @click="$emit('toggle-complete', task)" 
      class="text-lg cursor-pointer"
    >
      {{ task.title }}
    </span>
    <div class="space-x-2">
      <button 
        @click="$emit('edit', task)" 
        class="text-blue-500 hover:underline"
      >
        Edit
      </button>
      <button 
        @click="$emit('delete', task)" 
        class="text-red-500 hover:underline"
      >
        Delete
      </button>
    </div>
  </li>
</template> -->
