<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { landingContent } from "@/content/landingContent";

const activeIndex = ref(0);

const sections = landingContent.nav.links.map((link) =>
  link.href.replace("#", ""),
);

const handleScroll = () => {
  const scrollPos = window.scrollY + window.innerHeight / 2;

  sections.forEach((id, index) => {
    const el = document.getElementById(id);
    if (!el) return;

    const top = el.offsetTop;
    const bottom = top + el.offsetHeight;

    if (scrollPos >= top && scrollPos < bottom) {
      activeIndex.value = index;
    }
  });
};
// scroll do top / hero
const scrollToTop = () => {
  const el = document.getElementById("hero"); // Hero
  if (el) el.scrollIntoView({ behavior: "smooth" });
};

const isOpen = ref(false);

const toggleMenu = () => {
  isOpen.value = !isOpen.value;
};

const closeMenu = () => {
  isOpen.value = false;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  handleScroll();
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
  <nav class="fixed top-0 left-0 w-full z-50 transition-all duration-300">
    <div
      class="max-w-7xl mx-auto flex items-center bg-primary justify-between px-6 py-3 border-2 border-secondary rounded-2xl backdrop-blur-md"
    >
      <!-- LOGO -->
      <span class="cursor-pointer" @click="scrollToTop">
        <img src="/logo/x-w.png" alt="Fizjorazem" class="h-14 w-auto" />
      </span>

      <!-- DESKTOP MENU -->
      <ul class="hidden md:flex gap-8 font-Nohemi text-xl">
        <li
          v-for="(link, index) in landingContent.nav.links"
          :key="link.label"
          class="relative"
        >
          <a
            :href="link.href"
            @click="closeMenu"
            class="relative px-3 py-2 text-white transition-all duration-300 hover:text-accent hover:scale-110 hover:-translate-y-1"
            :class="activeIndex === index ? 'text-accent scale-110' : ''"
          >
            {{ link.label }}

            <span
              class="absolute left-0 -bottom-1 h-[2px] w-0 bg-accent transition-all duration-300"
              :class="activeIndex === index ? 'w-full' : ''"
            ></span>
          </a>
        </li>
      </ul>

      <!-- SOCIAL (desktop only) -->
      <div class="hidden md:flex gap-4 items-center">
        <a
          href="https://facebook.com"
          target="_blank"
          class="hover:scale-125 transition-all duration-300"
        >
          <img src="/external/Facebook.png" alt="Facebook" class="h-6" />
        </a>

        <a
          href="https://instagram.com"
          target="_blank"
          class="hover:scale-125 transition-all duration-300"
        >
          <img src="/external/Instagram.png" alt="Instagram" class="h-6" />
        </a>
      </div>

      <!-- HAMBURGER BUTTON -->
      <button
        @click="toggleMenu"
        class="md:hidden flex flex-col gap-1 w-8 h-8 justify-center items-center"
      >
        <span
          class="h-0.5 w-6 bg-white transition-all duration-300"
          :class="isOpen ? 'rotate-45 translate-y-2' : ''"
        ></span>
        <span
          class="h-0.5 w-6 bg-white transition-all duration-300"
          :class="isOpen ? 'opacity-0' : ''"
        ></span>
        <span
          class="h-0.5 w-6 bg-white transition-all duration-300"
          :class="isOpen ? '-rotate-45 -translate-y-2' : ''"
        ></span>
      </button>
    </div>

    <!-- MOBILE MENU -->
    <transition name="fade">
      <div
        v-if="isOpen"
        class="md:hidden bg-primary mt-2 mx-4 rounded-xl border border-secondary p-6 flex flex-col gap-6 text-center text-white font-Nohemi text-xl"
      >
        <a
          v-for="(link, index) in landingContent.nav.links"
          :key="link.label"
          :href="link.href"
          @click="closeMenu"
          class="transition-all duration-300 hover:text-accent"
          :class="activeIndex === index ? 'text-accent' : ''"
        >
          {{ link.label }}
        </a>

        <div class="flex justify-center gap-6 pt-4">
          <a href="https://facebook.com" target="_blank">
            <img src="/external/Facebook.png" class="h-6" />
          </a>
          <a href="https://instagram.com" target="_blank">
            <img src="/external/Instagram.png" class="h-6" />
          </a>
        </div>
      </div>
    </transition>
  </nav>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
