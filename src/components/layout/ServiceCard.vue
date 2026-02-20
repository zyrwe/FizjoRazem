<script setup>
defineProps({
  title: String, // Nazwa masażu
  description: String, // Opis co jest robione
  image: String, // Obrazek lub ikona (opcjonalne)
});
</script>

<template>
  <div class="group perspective w-full max-w-xs">
    <div
      class="relative w-full h-64 transition-transform duration-700 transform-style-preserve-3d group-hover:rotate-y-180"
    >
      <!-- FRONT SIDE -->
      <div
        class="absolute w-full h-full backface-hidden bg-white rounded-xl shadow-lg flex flex-col items-center justify-center p-4 bg-white/80 backdrop-blur-md border border-primary/30 hover:scale-105 hover:border-accent transition-all duration-300 shadow-lg hover:shadow-xl"
      >
        <img
          v-if="image"
          :src="image"
          alt=""
          class="h-20 w-20 mb-4 object-contain"
        />
        <h3
          class="text-xl font-Poppins font-bold mb-4 text-primary text-center"
        >
          {{ title }}
        </h3>
      </div>

      <!-- BACK SIDE -->
      <div
        class="absolute w-full h-full backface-hidden rotate-y-180 bg-primary rounded-xl shadow-lg flex items-center justify-center p-4"
      >
        <p class="text-white font-Poppins text-center">{{ description }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.perspective {
  perspective: 1000px;
}
.backface-hidden {
  backface-visibility: hidden;
}
.rotate-y-180 {
  transform: rotateY(180deg);
}
.transform-style-preserve-3d {
  transform-style: preserve-3d;
}
.group-hover\:rotate-y-180:hover {
  transform: rotateY(180deg);
}
</style>
