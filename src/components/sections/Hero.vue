<script setup>
import { landingContent } from "@/content/landingContent";

defineProps({
  id: { type: String, required: true },
});

const cases = [
  {
    label: "Ortopedycznych",
    bg: "bg-secondary",
    text: "text-primary",
    border: "border border-secondary/30",
    hover: "hover:bg-accent hover:text-white",
  },
  {
    label: "Reumatologicznych",
    bg: "bg-primary",
    text: "text-white",
    border: "border border-secondary/30",
    hover: "hover:bg-secondary hover:text-primary",
  },
  {
    label: "Neurologicznych",
    bg: "bg-accent",
    text: "text-white",
    border: "border border-secondary",
    hover: "hover:bg-primary hover:text-white",
  },
  {
    label: "Po amputacjach",
    bg: "bg-accent",
    text: "text-white",
    border: "border border-secondary",
    hover: "hover:bg-primary hover:text-white",
  },
  {
    label: "Onkologicznych",
    bg: "bg-secondary",
    text: "text-primary",
    border: "border border-secondary/30",
    hover: "hover:bg-accent hover:text-white",
  },
  {
    label: "Bóli napięciowych",
    bg: "bg-primary",
    text: "text-white",
    border: "border border-secondary/30",
    hover: "hover:bg-secondary hover:text-primary",
  },
  {
    label: "Mobilizacji seniorów",
    bg: "bg-primary",
    text: "text-white",
    border: "border border-secondary/30",
    hover: "hover:bg-secondary hover:text-primary",
  },
];
</script>

<template>
  <section
    :id="id"
    class="relative min-h-[100svh] flex items-center px-6 pt-24 md:pt-28 overflow-hidden"
  >
    <div
      class="max-w-7xl mx-auto w-full grid lg:grid-cols-2 gap-16 items-center sm:p-20"
    >
      <!-- LEWA STRONA -->
      <div>
        <h1
          class="font-Nohemi text-5xl md:text-6xl lg:text-7xl leading-[1.1] text-primary"
        >
          Fizjoterapia
          <br />
          <span class="text-ink">w Twoim domu</span>
        </h1>

        <div class="w-24 h-1 bg-accent mt-6 mb-8 rounded-full"></div>

        <p
          class="font-Poppins text-lg md:text-xl text-ink leading-relaxed max-w-xl"
        >
          Towarzyszymy pacjentom w drodze do wyzdrowienia i lepszego
          samopoczucia – bez bólu i ograniczeń ruchowych. Pracujemy z
          cierpliwością, zrozumieniem i profesjonalną opieką.
        </p>

        <div class="mt-10 flex flex-wrap gap-4">
          <a
            href="#services"
            class="bg-primary text-white px-8 py-4 rounded-xl font-Poppins text-lg shadow-lg hover:scale-105 hover:bg-accent transition-all duration-300"
          >
            Zobacz jak możemy pomóc
          </a>

          <a
            href="#contact"
            class="border-2 border-primary text-primary px-8 py-4 rounded-xl font-Poppins text-lg hover:bg-accent hover:text-white transition-all duration-300"
          >
            Skontaktuj się z nami
          </a>
        </div>
      </div>

      <!-- PRAWA STRONA -->
      <div class="relative">
        <h3 class="font-Nohemi text-2xl md:text-3xl text-primary mb-6">
          Pomagamy w przypadkach:
        </h3>

        <div class="flex flex-wrap gap-4">
          <span
            v-for="item in cases"
            :key="item.label"
            :class="[
              'px-6 py-3 rounded-full font-Poppins text-sm md:text-base font-semibold transition-all cursor-pointer duration-300',
              item.bg,
              item.text,
              item.border,
              item.hover,
            ]"
          >
            {{ item.label }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>
