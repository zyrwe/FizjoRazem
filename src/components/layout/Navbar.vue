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

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  handleScroll();
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
  <nav class="sticky top-0 z-50 transition-all duration-300">
    <div
      class="max-w-7xl mx-auto flex items-center bg-primary justify-between px-6 py-2 border-2 border-secondary rounded-2xl backdrop-blur-md"
    >
      <!-- LOGO po lewej -->
      <span class="cursor-pointer" @click="scrollToTop">
        <img src="/logo/x-w.png" alt="Fizjorazem" class="h-16 w-auto" />
      </span>

      <!-- MENU ŚRODEK -->
      <ul class="flex gap-8 font-Nohemi text-2xl">
        <li
          v-for="(link, index) in landingContent.nav.links"
          :key="link.label"
          class="relative"
        >
          <a
            :href="link.href"
            class="relative px-3 py-2 text-white font-medium transition-all duration-300 ease-out hover:text-accent hover:scale-110 hover:-translate-y-1"
            :class="activeIndex === index ? 'text-accent scale-110' : ''"
          >
            {{ link.label }}

            <span
              class="absolute left-0 -bottom-1 h-[2px] w-0 bg-accent transition-all duration-300"
              :class="activeIndex === index ? 'w-full' : 'group-hover:w-full'"
            ></span>
          </a>
        </li>
      </ul>

      <!-- RIGHT SIDE PLACEHOLDER / CTA -->
      <div class="flex gap-4 items-center">
        <a
          href="https://facebook.com"
          target="_blank"
          class="text-secondary hover:text-accent hover:scale-125 transition-all duration-300"
          ><img
            src="/external/Facebook.png"
            alt="Facebook"
            class="h-8 w-auto"
          />
          <i class="fa-brands fa-facebook text-2xl"></i>
        </a>

        <a
          href="https://instagram.com"
          target="_blank"
          class="text-secondary hover:text-accent hover:scale-125 transition-all duration-300"
        >
          <img
            src="/external/Instagram.png"
            alt="Instagram"
            class="h-8 w-auto"
          />
          <i class="fa-brands fa-instagram text-2xl"></i>
        </a>
      </div>
    </div>
  </nav>
</template>
