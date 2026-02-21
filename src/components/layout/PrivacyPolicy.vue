<script setup>
const emit = defineEmits(["closePrivacy"]);
</script>

<template>
  <section
    id="privacy"
    class="min-h-screen py-24 px-6 bg-gray-100 flex justify-center items-start"
  >
    <div class="max-w-3xl bg-white p-12 rounded-2xl shadow-lg">
      <h1 class="text-4xl font-bold text-primary mb-10">
        Polityka prywatności
      </h1>

      <div class="space-y-6 text-gray-800 leading-relaxed text-base">
        <p><strong>1. Administrator danych</strong></p>
        <p>
          Administratorem danych osobowych jest FizjoRazem.<br />
          E-mail: kontakt@fizjorazem.pl
        </p>

        <p><strong>2. Zakres przetwarzanych danych</strong></p>
        <p>
          Przetwarzamy dane przekazane dobrowolnie poprzez kontakt mailowy lub
          telefoniczny.
        </p>

        <p><strong>3. Cel przetwarzania</strong></p>
        <p>
          Dane wykorzystywane są wyłącznie w celu odpowiedzi na zapytanie oraz
          realizacji usług.
        </p>

        <p><strong>4. Prawa użytkownika</strong></p>
        <p>
          Masz prawo do dostępu, sprostowania, usunięcia danych oraz wniesienia
          skargi do Prezesa UODO.
        </p>

        <p><strong>5. Pliki cookies</strong></p>
        <p>
          Strona może wykorzystywać wyłącznie techniczne pliki cookies niezbędne
          do jej prawidłowego działania.
        </p>
      </div>

      <button
        @click="
          emit('closePrivacy');
          window.scrollTo({ top: 0, behavior: 'smooth' });
        "
        class="mt-8 px-6 py-3 bg-accent rounded-lg text-white hover:bg-accent/80 transition"
      >
        Powrót na stronę główną
      </button>
    </div>
  </section>
</template>
