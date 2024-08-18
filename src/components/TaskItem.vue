<template>
  <li :class="{ completed: task.completed }">
    <span @click="$emit('toggle-complete', task)">{{ task.title }}</span>
    <div>
      <button @click="$emit('edit', task)">Edit</button>
      <button @click="$emit('delete', task)">Delete</button>
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
      class="cursor-pointer text-lg"
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
