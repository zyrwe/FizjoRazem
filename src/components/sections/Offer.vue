<script setup>
import { ref, computed, watch } from "vue";

const activeTab = ref("individual");
const activeIndex = ref(0);

const individual = [
  {
    title: "Rehabilitacja domowa",
    description:
      "Kompleksowa rehabilitacja w domu pacjenta. Indywidualny plan terapii dostosowany do potrzeb i możliwości ruchowych.",
  },
  {
    title: "Terapia manualna",
    description:
      "Specjalistyczne techniki pracy z tkankami miękkimi oraz stawami, redukujące ból i przywracające mobilność.",
  },
  {
    title: "Masaż leczniczy",
    description:
      "Terapia manualna zmniejszająca napięcia mięśniowe, poprawiająca krążenie i przyspieszająca regenerację.",
  },
  {
    title: "Masaż leczniczy",
    description:
      "Terapia manualna zmniejszająca napięcia mięśniowe, poprawiająca krążenie i przyspieszająca regenerację.",
  },
  {
    title: "Masaż leczniczy",
    description:
      "Terapia manualna zmniejszająca napięcia mięśniowe, poprawiająca krążenie i przyspieszająca regenerację.",
  },
];

const company = [
  {
    title: "Pakiety dla pracowników",
    description:
      "Stała opieka fizjoterapeutyczna dla zespołów, zmniejszająca absencję i poprawiająca komfort pracy.",
  },
  {
    title: "Profilaktyka w miejscu pracy",
    description:
      "Działania zapobiegające przeciążeniom i urazom wynikającym z charakteru pracy.",
  },
  {
    title: "Warsztaty ergonomii",
    description:
      "Szkolenia z zakresu ergonomii stanowiska pracy i zdrowych nawyków ruchowych.",
  },
  {
    title: "Warsztaty ergonomii",
    description:
      "Szkolenia z zakresu ergonomii stanowiska pracy i zdrowych nawyków ruchowych.",
  },
  {
    title: "Warsztaty ergonomii",
    description:
      "Szkolenia z zakresu ergonomii stanowiska pracy i zdrowych nawyków ruchowych.",
  },
];

const currentItems = computed(() =>
  activeTab.value === "individual" ? individual : company,
);

const currentDescription = computed(
  () => currentItems.value[activeIndex.value].description,
);

// reset aktywnej pozycji przy zmianie zakładki
watch(activeTab, () => {
  activeIndex.value = 0;
});
</script>

<template>
  <section id="pricing" class="min-h-screen py-25 px-6 relative">
    <div class="max-w-5xl mx-auto text-center">
      <h2 class="text-4xl font-bold mb-12 text-ink">
        Nasza oferta
        <div class="w-24 mt-2 h-1 bg-accent mx-auto rounded-full"></div>
      </h2>

      <!-- Toggle -->
      <div class="relative inline-flex bg-primary/20 p-1 rounded-full">
        <div
          class="absolute top-1 bottom-1 w-1/2 bg-primary rounded-full transition-all duration-300"
          :class="activeTab === 'company' ? 'translate-x-full ' : ''"
        ></div>

        <button
          @click="activeTab = 'individual'"
          class="relative z-10 px-8 py-3 rounded-full font-medium transition-all duration-300 cursor-pointer"
          :class="activeTab === 'individual' ? 'text-light' : 'text-primary'"
        >
          Indywidualnie
        </button>

        <button
          @click="activeTab = 'company'"
          class="relative z-10 px-8 py-3 rounded-full font-medium transition-all duration-300 cursor-pointer"
          :class="activeTab === 'company' ? 'text-light' : 'text-primary '"
        >
          Dla firm
        </button>
      </div>
      <div class="relative mt-10">
        <transition name="fade" mode="out-in">
          <div
            :key="activeTab"
            class="grid md:grid-cols-2 gap-10 items-center border-2 border-secondary rounded-2xl p-10"
          >
            <!-- OPIS (dla firm odwrócony) -->
            <div
              :class="
                activeTab === 'company'
                  ? 'order-1 md:order-1'
                  : 'order-2 md:order-2'
              "
              class="bg-white rounded-2xl p-10 shadow-xl min-h-[250px] flex items-center"
            >
              <transition name="fade" mode="out-in">
                <p :key="activeIndex" class="text-lg text-ink leading-relaxed">
                  {{ currentDescription }}
                </p>
              </transition>
            </div>

            <!-- LISTA -->
            <div
              :class="
                activeTab === 'company'
                  ? 'order-2 md:order-2'
                  : 'order-1 md:order-1'
              "
              class="flex flex-col gap-4"
            >
              <div
                v-for="(item, index) in currentItems"
                :key="item.title"
                @click="activeIndex = index"
                class="cursor-pointer p-6 rounded-xl transition-all duration-300 border-2"
                :class="
                  activeIndex === index
                    ? 'bg-primary text-white border-primary scale-105 shadow-lg'
                    : 'bg-white border-secondary hover:scale-105'
                "
              >
                {{ item.title }}
              </div>
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
