<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <section class="text-center flex flex-col justify-center items-center h-96">
    <i class="pi pi-exclamation-triangle text-yellow-400 text-7xl mb-4"> </i>
    <h1 class="text-6xl font-bold mb-4">404 Not Found</h1>
    <p class="text-xl mb-5">This Page does not exist</p>
    <RouterLink
      to="/"
      class="bg-green-700 text-white px-3 py-2 mt-4 rounded-md hover:bg-green-900"
      >Go Back</RouterLink
    >
  </section>
</template>
