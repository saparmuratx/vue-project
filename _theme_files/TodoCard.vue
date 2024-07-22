<template>
  <div class="todo-card">
    <h2>{{ todo.title }}</h2>
    <button @click="deleteTodo(index)"> X </button>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

// Define the props that the component will accept
const props = defineProps({
  todo: {
    type: Object,
    required: true
  }
});


const emit = defineEmits(['todo-deleted']);


const deleteTodo = (index) => {
    emit("todo-deleted", {index})
};

</script>

<style scoped>
.todo-card {
  background-color: #2c3e50; /* Dark background color */
  border: 1px solid #ccc; /* Light border */
  border-radius: 8px; /* Rounded corners */
  padding: 16px;
  margin: 10px; /* Space between cards */
  text-align: center; /* Center text inside cards */
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Subtle shadow for depth */
  width: 200px; /* Fixed width for todo cards */
}

.todo-card h2 {
  margin: 0 0 10px; /* Space below the heading */
}

.todo-card p {
  margin: 5px 0; /* Space between paragraphs */
}
</style>