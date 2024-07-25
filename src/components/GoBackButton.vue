<script setup>
import { RouterLink } from 'vue-router';


defineProps({
  title: {
    type: String,
    default: "Go Back"
  }
})

</script>

<template>
  <!-- Go Back -->
  <section>
    <div class="container m-auto py-6 px-6">
      <!-- <RouterLink :to="link" class="text-green-500 hover:text-green-600 flex items-center"> -->
      <div class="text-green-500 hover:text-green-600 flex items-center">
        <i class="pi pi-arrow-circle-left mr-3"></i> {{ title }}
      </div>
      <!-- </RouterLink> -->
    </div>
  </section>
</template>