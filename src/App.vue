<script setup>
import { ref } from "vue";
import Navbar from "@/components/layout/Navbar.vue";
import Home from "@/views/Home.vue";
import ScrollDots from "@/components/layout/ScrollDots.vue";
import Footer from "@/components/layout/Footer.vue";
import PrivacyPolicy from "@/components/layout/PrivacyPolicy.vue";

const showPrivacy = ref(false);

const openPrivacy = () => {
  showPrivacy.value = true;
};

const closePrivacy = () => {
  showPrivacy.value = false;
};
</script>

<template>
  <div>
    <main class="relative">
      <template v-if="showPrivacy">
        <PrivacyPolicy @closePrivacy="closePrivacy" />
      </template>
      <template v-else>
        <Navbar />
        <Home />
        <ScrollDots />
      </template>
    </main>
    <Footer @privacyClick="openPrivacy" />
  </div>
</template>
