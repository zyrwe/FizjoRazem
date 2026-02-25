<script setup>
import ServiceCard from "@/components/layout/ServiceCard.vue";
import { services } from "@/content/servicesData.js";
</script>

<template>
  <section id="services" class="py-25 px-6 relative">
    <h2 class="text-4xl md:text-5xl font-bold text-center mb-5 text-ink">
      Nasze metody pracy
      <div class="w-24 mt-2 h-1 bg-accent mx-auto rounded-full"></div>
    </h2>
    <div
      class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 lg:grid-cols-4 gap-4 justify-items-center max-w-[1200px] mx-auto"
    >
      <ServiceCard
        v-for="(service, index) in services"
        :key="index"
        :title="service.title"
        :description="service.description"
        :image="service.image"
      />
    </div>
  </section>
</template>
