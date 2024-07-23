<script setup>
import { RouterLink } from 'vue-router';  
</script>

<template>
  <section class="text-center flex flex-col justify-center items-center h-96">
    <i class="pi pi-exclamation-triangle mb-4" style="font-size: 5.5rem;font-style: bold; color: #c2410c"></i>
    <h1 class="text-7xl font-bold mb-4">404 Not Found</h1>
    <p class="text-xl mb-5">This page does not exist</p>
    <RouterLink to="/" class="text-white bg-green-700 hover:bg-green-900 rounded-md px-3 py-2 mt-4">Go Back</RouterLink>
  </section>
</template>