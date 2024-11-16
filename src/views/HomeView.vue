<script setup>
import Hero from "@/components/Hero.vue";
import HomeCards from "@/components/HomeCards.vue";
import JobLIst from "@/components/JobLIst.vue";
</script>

<template>
  <Hero />
  <HomeCards />
  <JobLIst :limit="3" :shawButton="true" />
</template>
