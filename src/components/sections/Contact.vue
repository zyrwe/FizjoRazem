<script setup>
import { computed } from "vue";

import Booksy from "@/assets/card/Booksy.png";
import card1 from "@/assets/card/card1.png";
import card2 from "@/assets/card/card2.png";

const isMobile = /Android|iPhone|iPad|iPod/i.test(navigator.userAgent);

const phoneOrMail1 = computed(() =>
  isMobile ? "tel:455505027" : "mailto:fizjorazem@gmail.com",
);

const phoneOrMail2 = computed(() =>
  isMobile ? "tel:455408009" : "mailto:fizjorazem@gmail.com",
);
</script>

<template>
  <section :id="id" class="min-h-screen py-20 px-6 bg-[--color-light]">
    <div class="text-center">
      <h2
        class="text-3xl md:text-4xl font-Poppins py-15 font-bold text-[--color-ink]"
      >
        Skontaktuj się z nami!
        <div class="w-24 mt-2 h-1 bg-accent mx-auto rounded-full"></div>
      </h2>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-16 max-w-6xl mx-auto">
      <div class="card-wrapper">
        <a :href="phoneOrMail1">
          <img
            :src="card1"
            alt="Wizytówka 1"
            class="contact-card contact-card1"
          />
        </a>
      </div>

      <div class="card-wrapper">
        <a :href="phoneOrMail2">
          <img
            :src="card2"
            alt="Wizytówka 2"
            class="contact-card contact-card2"
          />
        </a>
      </div>
    </div>
    <div
      class="text-center grid grid-cols-1 md:grid-cols-1 max-w-6xl mx-auto mt-15"
    >
      <h2
        class="text-3xl md:text-4xl font-Poppins font-bold mb-8 text-[--color-ink]"
      >
        lub zarezerwuj wizytę w booksy!
      </h2>
      <div class="flex justify-center">
        <a
          href="https://www.booksy.com/pl-pl/booking/fizjorazem-1"
          class="relative w-[350px] md:w-[550px] group b-order-2 bg-primary p-8 border-primary rounded-xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300"
        >
          <!-- OBRAZEK -->
          <img :src="Booksy" alt="Booksy" class="w-full h-auto block" />
        </a>
      </div>
    </div>
  </section>
</template>
