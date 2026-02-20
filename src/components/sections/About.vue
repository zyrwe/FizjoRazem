<script setup>
import { landingContent } from "@/content/landingContent";

defineProps({
  id: { type: String, required: true },
});
</script>

<template>
  <section
    :id="id"
    class="min-h-screen flex items-center justify-center px-6 py-32 bg-white"
  >
    <div class="max-w-5xl w-full">
      <!-- NAGŁÓWEK -->
      <div class="text-center mb-20">
        <h2
          class="font-Nohemi text-4xl md:text-5xl lg:text-6xl text-primary mb-6"
        >
          {{ landingContent.about.title }}
        </h2>

        <div class="w-24 mt-2 h-1 bg-accent mx-auto rounded-full"></div>
      </div>

      <!-- TREŚĆ -->
      <div class="grid md:grid-cols-2 gap-12 items-center">
        <!-- LEWA STRONA - TEKST -->
        <div class="space-y-8">
          <div
            v-for="(line, index) in landingContent.about.text"
            :key="index"
            class="flex items-start gap-4"
          >
            <div class="mt-2 w-3 h-3 rounded-full bg-accent shrink-0"></div>

            <p
              class="font-Poppins text-lg md:text-xl text-ink leading-relaxed"
              v-html="line"
            ></p>
          </div>
        </div>

        <!-- PRAWA STRONA - BLOK STYLISTYCZNY -->
        <div
          class="bg-primary text-white rounded-3xl p-12 shadow-xl relative overflow-hidden"
        >
          <p class="font-Poppins text-xl md:text-2xl leading-relaxed">
            Wierzymy, że skuteczna terapia zaczyna się od relacji. <br />
            Działamy z empatią, uważnością i profesjonalizmem.
          </p>

          <div
            class="absolute -bottom-10 -right-10 w-40 h-40 bg-secondary/20 rounded-full blur-2xl"
          ></div>
        </div>
      </div>
    </div>
  </section>
</template>
