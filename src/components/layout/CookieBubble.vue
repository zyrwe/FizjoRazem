<script setup>
import { ref, onMounted } from "vue";

const visible = ref(false);

onMounted(() => {
  if (!localStorage.getItem("cookiesAccepted")) {
    setTimeout(() => (visible.value = true), 1500);
  }
});

const acceptCookies = () => {
  localStorage.setItem("cookiesAccepted", "true");
  visible.value = false;
};

const rejectCookies = () => {
  localStorage.setItem("cookiesAccepted", "rejected");
  visible.value = false;
};
</script>

<template>
  <transition name="fade">
    <div
      v-if="visible"
      class="fixed bottom-6 right-6 z-50 w-80 bg-white border border-secondary shadow-xl rounded-2xl p-6"
    >
      <p class="text-sm text-ink mb-4">
        Ta strona może wykorzystywać pliki cookies w celu poprawy działania i
        analizy ruchu. Możesz zaakceptować lub odrzucić ich użycie.
      </p>

      <div class="flex gap-3">
        <button
          @click="acceptCookies"
          class="flex-1 bg-primary text-white py-2 rounded-lg hover:bg-accent transition"
        >
          Akceptuję
        </button>

        <button
          @click="rejectCookies"
          class="flex-1 border border-primary text-primary py-2 rounded-lg hover:bg-primary hover:text-white transition"
        >
          Odrzucam
        </button>
      </div>
    </div>
  </transition>
</template>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>
