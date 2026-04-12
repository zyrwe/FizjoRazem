<script setup>
import { ref, computed, watch } from "vue";

const activeTab = ref("individual");
const activeIndex = ref(0);

const individual = [
  {
    title: "Rehabilitacja domowa",
    description:
      "Cena 200 zł za wizytę plus opłata za dojazd powyżej 10 km. Możliwe bonusy za wykupienie zabiegów powyżej 7 wizyt (ustalane indywidualnie)",
  },
  {
    title: "Masaż leczniczy",
    description:
      "Kręgosłup cały (45–60 min) 150 zł. Kręgosłup szyjny i obręcz barkowa 150 zł. + dojazd",
  },
  {
    title: "Drenaż limfatyczny",
    description: "Kończyny dolne 150–200 zł. Kończyna górna 150 zł. + dojazd",
  },
  {
    title: "Masaż Kobido",
    description: "200 zł. Transbukalny 250 zł. + dojazd",
  },
  {
    title: "Kinesiotaping",
    description: "40–70 zł. Cena zależna od obszaru.",
  },
  {
    title: "Bańki",
    description: "150 zł + dojazd",
  },
  {
    title: "Pinoterapia",
    description: "Cena ustalana indywidualnie",
  },
];

const company = [
  {
    title: "Pakiety dla pracowników",
    description:
      "Stała opieka fizjoterapeutyczna dla zespołów. Zmniejszenie absencji. Poprawa komfortu pracy.",
  },
  {
    title: "Profilaktyka w miejscu pracy",
    description: "Zapobieganie przeciążeniom. Lepsza ergonomia. Mniej urazów.",
  },
  {
    title: "Warsztaty ergonomii",
    description: "Szkolenia ergonomiczne. Zdrowe nawyki ruchowe.",
  },
  {
    title: "Masaż biurowy",
    description: "10–20 minut. Kark, plecy, ramiona. Redukcja stresu i bólu.",
  },
];

const currentItems = computed(() =>
  activeTab.value === "individual" ? individual : company,
);

const currentDescription = computed(
  () => currentItems.value[activeIndex.value].description,
);

watch(activeTab, () => {
  activeIndex.value = 0;
});
</script>

<template>
  <section id="pricing" class="min-h-screen py-25 px-6">
    <div class="max-w-6xl mx-auto text-center">
      <h2 class="text-4xl font-bold mb-12 text-ink">
        Nasza oferta
        <div class="w-24 mt-2 h-1 bg-accent mx-auto rounded-full"></div>
      </h2>

      <!-- TOGGLE -->
      <div class="relative inline-flex bg-primary/20 p-1 rounded-full">
        <div
          class="absolute top-1 bottom-1 w-1/2 bg-primary rounded-full transition-all duration-300"
          :class="activeTab === 'company' ? 'translate-x-full' : ''"
        ></div>

        <button
          @click="activeTab = 'individual'"
          class="relative z-10 px-8 py-3 rounded-full"
          :class="activeTab === 'individual' ? 'text-white' : 'text-primary'"
        >
          Indywidualnie
        </button>

        <button
          @click="activeTab = 'company'"
          class="relative z-10 px-8 py-3 rounded-full"
          :class="activeTab === 'company' ? 'text-white' : 'text-primary'"
        >
          Dla firm
        </button>
      </div>

      <!-- CONTENT -->
      <div class="mt-10">
        <transition name="fade" mode="out-in">
          <div
            :key="activeTab"
            class="grid md:grid-cols-2 gap-10 border-2 border-secondary rounded-2xl p-6 md:p-10 min-h-[500px]"
          >
            <!-- OPIS FULL HEIGHT -->
            <div
              :class="activeTab === 'company' ? 'order-1' : 'order-2'"
              class="hidden md:flex h-full"
            >
              <transition name="fade" mode="out-in">
                <div
                  :key="activeIndex"
                  class="w-full h-full bg-white rounded-3xl p-8 shadow-xl border border-secondary/50 flex flex-col justify-between"
                >
                  <!-- TOP -->
                  <div>
                    <h3 class="text-2xl font-bold text-primary mb-4">
                      {{ currentItems[activeIndex].title }}
                    </h3>

                    <div class="w-16 h-1 bg-accent mb-6 rounded-full"></div>

                    <div class="space-y-3 text-ink leading-relaxed">
                      <p
                        v-for="(line, i) in currentDescription.split('.')"
                        :key="i"
                        class="flex gap-3"
                      >
                        <span
                          class="mt-2 w-2 h-2 bg-accent rounded-full"
                        ></span>
                        <span>{{ line.trim() }}</span>
                      </p>
                    </div>
                  </div>
                </div>
              </transition>
            </div>

            <!-- LISTA -->
            <div
              :class="activeTab === 'company' ? 'order-2' : 'order-1'"
              class="flex flex-col gap-4"
            >
              <div
                v-for="(item, index) in currentItems"
                :key="item.title"
                @click="activeIndex = index"
                class="cursor-pointer rounded-xl transition-all duration-300 border-2"
                :class="
                  activeIndex === index
                    ? 'bg-primary text-white border-primary shadow-lg scale-[1.02]'
                    : 'bg-white border-secondary hover:shadow-md hover:-translate-y-1'
                "
              >
                <div class="p-6 font-medium">
                  {{ item.title }}
                </div>

                <!-- MOBILE -->
                <div
                  class="md:hidden transition-all duration-300 overflow-hidden"
                  :class="
                    activeIndex === index ? 'max-h-60 p-6 pt-0' : 'max-h-0'
                  "
                >
                  <p class="text-sm leading-relaxed whitespace-pre-line">
                    {{ item.description }}
                  </p>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<style>
.fade-enter-active {
  transition: all 0.3s ease;
}
.fade-leave-active {
  transition: all 0.2s ease;
}
.fade-enter-from {
  opacity: 0;
  transform: translateY(10px);
}
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
