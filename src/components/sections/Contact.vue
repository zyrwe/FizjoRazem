<template>
  <section :id="id" class="min-h-screen py-20 px-6 bg-[--color-light]">
    <div class="text-center">
      <h2
        class="text-3xl md:text-4xl font-Poppins py-15 font-bold mb-8 text-[--color-ink]"
      >
        Zadzwoń do nas !
      </h2>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-16 max-w-6xl mx-auto">
      <!-- Wizytówka 1 -->
      <div class="card-wrapper">
        <img
          src="/card/card1.png"
          alt="Wizytówka 1"
          class="contact-card contact-card1"
        />
      </div>

      <!-- Wizytówka 2 -->
      <div class="card-wrapper">
        <img
          src="/card/card2.png"
          alt="Wizytówka 2"
          class="contact-card contact-card2"
        />
      </div>
    </div>
    <div
      class="text-center grid grid-cols-1 md:grid-cols-1 max-w-6xl mx-auto mt-15"
    >
      <h2
        class="text-3xl md:text-4xl font-Poppins font-bold mb-8 text-[--color-ink]"
      >
        lub napisz
      </h2>
      <div
        class="flex mx-auto p-6 justify-center gap-6 mb-6 border-2 bg-secondary border-secondary hover:text-accent contact-card contact-mail"
      >
        <a
          href="mailto:kontakt@fizjorazem.pl"
          class="text-3xl transition-colors duration-300 text-primary font-Nohemi"
        >
          kontakt@fizjorazem.pl
        </a>
      </div>
    </div>
  </section>
</template>
