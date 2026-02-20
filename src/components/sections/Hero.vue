<script setup>
import { landingContent } from "@/content/landingContent";

defineProps({
  id: { type: String, required: true },
});
</script>

<template>
  <section
    :id="id"
    class="min-h-screen flex flex-col pt-25 items-center px-6 relative"
  >
    <h1 class="text-5xl md:text-6xl lg:text-7xl font-Nohemi mb-6 leading-tight">
      {{ landingContent.hero.title }}
      <div class="w-24 mt-2 h-1 bg-accent mx-auto rounded-full"></div>
    </h1>
    <p class="text-lg md:text-xl mb-6">{{ landingContent.hero.subtitle }}</p>
    <a
      href="#services"
      class="bg-primary text-light px-8 py-4 rounded-xl text-lg hover:scale-105 hover:bg-accent transition-all duration-300 shadow-lg"
    >
      {{ landingContent.hero.cta }}
    </a>
  </section>
</template>
