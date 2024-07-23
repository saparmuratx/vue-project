<script setup>
import Hero from './components/Hero.vue';
import HomeCards from './components/HomeCards.vue';
import JobListings from './components/JobListings.vue';
import Navbar from './components/Navbar.vue';

</script>


<template>
  <Navbar />
  <Hero />
  <HomeCards />
  <JobListings limit="7" :showButton="true" />
</template>


<style scoped>
/* Optional: Add custom styles here */
</style>
