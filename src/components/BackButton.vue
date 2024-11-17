<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <section>
    <div class="container m-auto py-6 px-6">
      <RouterLink
        to="/jobs"
        class="text-indigo-500 hover:text-indigo-600 flex items-center"
      >
        Back to Job Listings
      </RouterLink>
    </div>
  </section>
</template>
