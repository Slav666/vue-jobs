<script setup>
import navBar from "@/components/navBar.vue";
import Hero from "@/components/Hero.vue";
import HomeCards from "./components/HomeCards.vue";
import JobLIst from "./components/JobLIst.vue";
</script>

<template>
  <navBar />
  <Hero />
  <HomeCards />
  <JobLIst :limit="3" :shawButton="true" />
  <!-- <h1 class="text-red-500">View jobs</h1> -->
</template>
