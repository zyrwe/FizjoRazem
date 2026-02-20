<script setup>
import { ref } from "vue";

const activeTab = ref("individual");

const individual = [
  "Rehabilitacja domowa",
  "Terapia manualna",
  "Masaż leczniczy",
];

const company = [
  "Pakiety dla pracowników",
  "Profilaktyka w miejscu pracy",
  "Warsztaty ergonomii",
];
</script>

<template>
  <section id="pricing" class="min-h-screen py-40 px-6 relative">
    <div class="max-w-5xl mx-auto text-center">
      <h2 class="text-4xl font-bold mb-12 text-ink">Współpraca</h2>

      <!-- Toggle -->
      <div class="relative inline-flex bg-primary/20 p-1 rounded-full mb-5">
        <div
          class="absolute top-1 bottom-1 w-1/2 bg-primary rounded-full transition-all duration-300"
          :class="activeTab === 'company' ? 'translate-x-full' : ''"
        ></div>

        <button
          @click="activeTab = 'individual'"
          class="relative z-10 px-8 py-3 rounded-full font-medium transition-all duration-300"
          :class="activeTab === 'individual' ? 'text-light' : 'text-primary'"
        >
          Indywidualnie
        </button>

        <button
          @click="activeTab = 'company'"
          class="relative z-10 px-8 py-3 rounded-full font-medium transition-all duration-300"
          :class="activeTab === 'company' ? 'text-light' : 'text-primary'"
        >
          Dla firm
        </button>
      </div>
      <div class="relative">
        <transition name="fade" mode="out-in">
          <div
            :key="activeTab"
            class="grid md:grid-cols-2 gap-8 border-2 border-secondary rounded-2xl p-8"
          >
            <div
              v-for="(item, index) in activeTab === 'individual'
                ? individual
                : company"
              :key="index"
              class="p-8 bg-white rounded-2xl shadow-lg hover:scale-105 transition-all duration-300"
            >
              {{ item }}
            </div>
          </div>
        </transition>
      </div>
      <!-- Content -->
    </div>
  </section>
</template>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
