<script setup>
import ServiceCard from "@/components/layout/ServiceCard.vue";
import { services } from "@/content/servicesData.js";
</script>

<template>
  <section id="services" class="py-35 px-6 relative">
    <h2 class="text-4xl md:text-5xl font-bold text-center mb-16 text-ink">
      Nasze metody pracy
    </h2>
    <div
      class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-3 gap-4 justify-items-center"
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
