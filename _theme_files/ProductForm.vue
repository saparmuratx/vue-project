<template>
  <div class="product-form">
    <h2>{{ name }}</h2>
    <form @submit.prevent="addProduct">
      <div>
        <label for="name">Product Name:</label>
        <input type="text" v-model="newProduct.name" required />
      </div>
      <div>
        <label for="description">Description:</label>
        <input type="text" v-model="newProduct.description" required  />
      </div>
      <div>
        <label for="vendor">Vendor:</label>
        <input type="text" v-model="newProduct.vendor" required />
      </div>
      <div>
        <label for="price">Price:</label>
        <input type="number" v-model="newProduct.price" required min="0" step="0.01" />
      </div>
      <button type="submit">Add Product</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const emit = defineEmits(['product-added']);

const name = "Add New Product";
const newProduct = ref({
      name: '',
      description: '',
      vendor: '',
      price: 0
    });

const addProduct = () => {
  emit('product-added', { ...newProduct.value, id: Date.now() });
  newProduct.value.name = '';
  newProduct.value.vendor = '';
  newProduct.value.description = '';
  newProduct.value.price = null;
};

</script>

<style>
.product-form {
  margin-bottom: 20px;
}

.product-form form {
  display: flex;
  flex-direction: column;
}

.product-form div {
  margin-bottom: 10px;
}
</style>