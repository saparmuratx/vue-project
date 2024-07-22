<template>
  <div class="product-card">
    <h2>{{index}} - {{ product.name }}</h2>
    <p>Vendor: {{ product.vendor }}</p>
    <p>Price: {{ product.price.toFixed(2) }}$</p>
    <button @click="deleteItem(index)"> X </button>
</div>

</template>

<script setup>

import { defineProps } from 'vue';

// Define the props that the component will accept
const props = defineProps({
  product: {
    type: Object,
    required: true
  },
  index: {
    type: Number,
    required: true
  }
});


const emit = defineEmits(['product-deleted']);


const deleteItem = (index) => {
    emit("product-deleted", {index})
};

</script>

<style scoped>
.product-card {
  background-color: #133f58; /* Dark background color */
  border: 1px solid #ccc; /* Light border */
  border-radius: 8px; /* Rounded corners */
  padding: 16px;
  margin: 10px; /* Space between cards */
  text-align: center; /* Center text inside cards */
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Subtle shadow for depth */
  width: 200px; /* Fixed width for product cards */
}

.product-card h2 {
  margin: 0 0 10px; /* Space below the heading */
}

.product-card p {
  margin: 5px 0; /* Space between paragraphs */
}
</style>