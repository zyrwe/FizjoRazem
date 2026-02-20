<script setup>
defineProps({
  name: String,
  role: String,
  email: String,
  phone: String,
});
</script>

<template>
  <div
    class="w-full p-10 rounded-3xl bg-white border border-primary/30 shadow-lg hover:shadow-2xl hover:scale-105 transition-all duration-300"
  >
    <h3 class="text-2xl font-bold text-primary mb-2">
      {{ name }}
    </h3>

    <p class="text-accent mb-4 font-medium">
      {{ role }}
    </p>

    <div class="space-y-2 text-ink">
      <p>{{ email }}</p>
      <p>{{ phone }}</p>
    </div>
  </div>
</template>
