<script setup>
import jobsData from "@/jobs.json"; // Import JSON
import { ref, defineProps } from "vue"; // Import ref for reactivity
import JobSingle from "./JobSingle.vue";

const jobs = ref(jobsData.jobs);
defineProps({
  limit: Number,
  shawButton: {
    type: Boolean,
    default: false,
  },
});
console.log(jobs.value); // Check that it logs the jobs array
</script>

<template>
  <section class="bg-blue-50 px-4 py-10">
    <div class="container-xl lg:container m-auto">
      <h2 class="text-3xl font-bold text-indigo-500 mb-6 text-center">
        Browse jobs
      </h2>
      <div class="grid grid-cols-1 gap-6 md:grid-cols-3">
        <!-- <JobSingle>{{ job.title }}</JobSingle> -->
        <JobSingle
          v-for="job in jobs.slice(0, limit || limit.length)"
          :key="job.id"
          :job="job"
        />
      </div>
    </div>
  </section>
  <section class="m-auto max-w-lg my-10 px-6" v-if="shawButton">
    <a
      href="/jobs"
      class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
      >View All Jobs</a
    >
  </section>
</template>
