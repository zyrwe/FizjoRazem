<script setup>
const emit = defineEmits(["privacyClick"]); // deklarujesz jakie eventy Footer emituje

const handleClick = () => {
  emit("privacyClick");
  window.scrollTo({ top: 0, behavior: "smooth" }); // dodaje scroll do góry
};
</script>
<template>
  <footer class="bg-primary text-light py-16 px-6 mt-24">
    <div class="max-w-7xl mx-auto grid md:grid-cols-3 gap-12">
      <!-- Logo + opis -->
      <div>
        <h3 class="text-2xl font-bold mb-4">Fizjorazem</h3>
        <p class="opacity-80">Profesjonalna fizjoterapia w Twoim domu.</p>
        <button
          @click="handleClick"
          class="text-light hover:underline pt-4 block"
        >
          Polityka prywatności
        </button>
      </div>

      <!-- Kontakt -->
      <div>
        <h4 class="font-semibold mb-4">Kontakt</h4>
        <p>+48 455 505 027</p>
        <p>+48 455 408 009</p>
        <p>kontakt@fizjorazem.pl</p>
      </div>

      <!-- Dane firmy -->
      <div>
        <h4 class="font-semibold mb-4">Dane firmy</h4>
        <p>Fizjorazem Sp. z o.o.</p>
        <p>NIP: 0000000000</p>
        <p>REGON: 000000000</p>
      </div>
    </div>

    <div class="text-center mt-12 opacity-70 text-sm">
      © 2026 Fizjorazem. Wszelkie prawa zastrzeżone.
    </div>
  </footer>
</template>
