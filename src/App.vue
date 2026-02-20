<script setup>
import Navbar from "@/components/layout/Navbar.vue";
import Home from "@/views/Home.vue";
import ScrollDots from "@/components/layout/ScrollDots.vue";
</script>

<template>
  <div>
    <Navbar />
    <main class="relative">
      <Home />
      <ScrollDots />
    </main>
    <div class="background-circles">
      <div v-for="n in 18" :key="n" class="circle"></div>
    </div>

    <RouterView />
  </div>
</template>
