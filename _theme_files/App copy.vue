<script setup>

import {onMounted, ref } from 'vue';
import ProductForm from './components/ProductForm.vue';
import ProductCard from './components/ProductCard.vue';
import TodoCard from './components/TodoCard.vue';

const name = ref("Ezio");
const newName = ref("");
const status = ref(true);


const products = ref([
        {
            "id": 1,
            "name": "Wireless Headphones",
            "description": "High-quality wireless headphones with noise cancellation",
            "price": 99.99,
            "vendor": "Bose"
        },
        {
            "id": 2,
            "name": "Smartwatch",
            "description": "Sleek and feature-packed smartwatch with fitness tracking",
            "price": 149.99,
            "vendor": "Apple"
        },
        {
            "id": 3,
            "name": "Gaming Mouse",
            "description": "Precision gaming mouse with customizable buttons and RGB lighting",
            "price": 59.99,
            "vendor": "Logitech"
        },
        {
            "id": 4,
            "name": "Portable Bluetooth Speaker",
            "description": "Powerful and portable Bluetooth speaker with long battery life",
            "price": 79.99,
            "vendor": "JBL"
        },
        {
            "id": 5,
            "name": "Fitness Tracker",
            "description": "Lightweight and water-resistant fitness tracker with heart rate monitoring",
            "price": 49.99,
            "vendor": "Fitbit"
        }
    ]);


const todos = ref([])

const toggleButton = () => {
    status.value = !status.value;
}; 

const addProduct = (product) => {
    console.log(product)
    products.value.push(product);
};

const deleteItem = (index) => {  
    products.value.splice(index, 1)
};

const deleteTodo = (index) => {
    
    todos.value.splice(index, 1)
};

const changeName = () => {
    name.value = newName.value
};

const apiUrl = "http://167.71.8.220:8000/api/inventory/items/";

onMounted(async () => {
    try {
        const response = await fetch("https://jsonplaceholder.typicode.com/todos");
        const data = await response.json();
        // console.log(data)
        todos.value = data
    } catch (error) {
        
    }
});


</script>

<template>
    
    <h1>Vue Store innit? {{ name }}</h1>

    <form @submit.prevent="changeName">
        <label for="name">Name</label>
        <input type="text" v-model="newName" required />
        <button type="submit"> Change name </button>
    </form>

    <p class="status-active" v-if="status"> User is active</p>
    <p class="status-inactive" v-else> User is inactive</p>
    <button @click="toggleButton"> Toggle Active </button>
    
    <h2>Product List</h2>
    <ProductCard 
    v-for="(product, index) in products" 
        :key="product.id" 
        :index="index" 
        :product="product"
        @product-deleted="deleteItem(index)"
    />

    <br>

    <div>
        <ProductForm @product-added="addProduct"/>
    </div>    
    
    <h2>Todo List</h2>

    <TodoCard
        v-for="(todo, index) in todos" 
        :key="todo.id"
        :todo = "todo"
        @todo-deleted="deleteTodo(index)"
    />


</template>

<style>
.status-active {
    color: green;
}

.status-inactive {
    color: rgb(212, 1, 1);
}


.product-list {
  background-color: #2c3e50; /* Dark background color */
  border: 1px solid #ccc; /* Light border */
  border-radius: 8px; /* Rounded corners */
  padding: 16px;
  margin: 10px; /* Space between cards */
  text-align: center; /* Center text inside cards */
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Subtle shadow for depth */
  width: 400px; /* Fixed width for product cards */
}

.product-card h2 {
  margin: 0 0 10px; /* Space below the heading */
}

.product-card p {
  margin: 5px 0; /* Space between paragraphs */
}


</style>