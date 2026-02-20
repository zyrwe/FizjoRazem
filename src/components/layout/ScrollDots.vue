<template>
  <div
    class="fixed top-1/2 right-6 transform -translate-y-1/2 flex flex-col gap-3 z-50"
  >
    <button
      v-for="(section, index) in sections"
      :key="section.id"
      @click="scrollToSection(section.id)"
      :class="[
        'w-4 h-4 rounded-full bg-secondary border border-primary cursor-pointer hover:bg-accent transition-transform duration-300',
        activeIndex === index ? 'bg-accent scale-150' : '',
      ]"
    ></button>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const sections = [
  { id: "hero" },
  { id: "about" },
  { id: "services" },
  { id: "offer" },
  { id: "contact" },
];

const activeIndex = ref(0);

const scrollToSection = (id) => {
  const el = document.getElementById(id);
  if (el) el.scrollIntoView({ behavior: "smooth" });
};

const handleScroll = () => {
  const scrollPos = window.scrollY + window.innerHeight / 2;
  sections.forEach((sec, index) => {
    const el = document.getElementById(sec.id);
    if (!el) return;
    const top = el.offsetTop;
    const bottom = top + el.offsetHeight;
    if (scrollPos >= top && scrollPos < bottom) {
      activeIndex.value = index;
    }
  });
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  handleScroll();
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped></style>
