<script setup>
// import jobsData from "@/jobs.json"; // Import JSON
import { ref, defineProps, onMounted, reactive } from "vue"; // Import ref for reactivity
import JobSingle from "./JobSingle.vue";
import { RouterLink } from "vue-router";
import PulseLoader from "vue-spinner/src/PulseLoader.vue";
import axios from "axios";

// const jobs = ref(jobsData.jobs);
defineProps({
  limit: Number,
  shawButton: {
    type: Boolean,
    default: false,
  },
});

const state = reactive({
  jobs: [],
  isLoading: true,
});

onMounted(async () => {
  try {
    const response = await axios.get("http://localhost:8000/jobs");
    state.jobs = response.data;
  } catch (error) {
    console.error("Error fetching jobs", error);
  } finally {
    state.isLoading = false;
  }
});

// console.log(jobs.value); // Check that it logs the jobs array
</script>

<template>
  <section class="bg-blue-50 px-4 py-10">
    <div class="container-xl lg:container m-auto">
      <h2 class="text-3xl font-bold text-indigo-500 mb-6 text-center">
        Browse jobs
      </h2>
      <!-- Loading spinner -->
      <div v-if="state.isLoading" class="text-center text-gray-500 py-6">
        <PulseLoader />
      </div>
      <div v-else class="grid grid-cols-1 gap-6 md:grid-cols-3">
        <!-- <JobSingle>{{ job.title }}</JobSingle> -->
        <JobSingle
          v-for="job in state.jobs.slice(0, limit || state.jobs.length)"
          :key="job.id"
          :job="job"
        />
      </div>
    </div>
  </section>
  <section class="m-auto max-w-lg my-10 px-6" v-if="shawButton">
    <RouterLink
      to="/jobs"
      class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
      >View All Jobs</RouterLink
    >
  </section>
</template>
