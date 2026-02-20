<script setup>
import { landingContent } from "@/content/landingContent";

defineProps({
  id: { type: String, required: true },
});
</script>

<template>
  <section
    :id="id"
    class="min-h-screen flex items-center justify-center px-6 text-dark"
  >
    <div class="max-w-3xl text-center">
      <h1 class="text-3xl md:text-4xl font-bold mb-4">
        {{ landingContent.about.title }}
      </h1>
      <p class="text-lg md:text-xl">{{ landingContent.about.text }}</p>
    </div>
  </section>
</template>
