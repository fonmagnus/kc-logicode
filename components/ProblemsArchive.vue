<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0.6]">
    <div
      id="problems-archive"
      class="flex flex-col h-full justify-center items-center p-6 gap-6 sm:px-24 md:px-48 lg:px-72 xl:px-96 min-h-screen"
    >
      <h1
        class="opacity-0 problems-archive-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
      >
        Arsip Soal Logicode
      </h1>

      <div
        class="flex flex-col border border-slate-200 shadow-md px-4 py-2 rounded-lg w-full"
      >
        <h3 class="text-orange-400 font-bold font-mono sm:text-lg md:text-xl">
          Logicode 2024
        </h3>
        <ul>
          <li>
            <a
              href="https://portal.kokocoder.com/contests/quiz/logicode-2024-qualification-round-1"
              target="_blank"
              class="text-slate-600 text-sm sm:text-md md:text-lg underline"
            >
              <i class="bx bx-link-external"></i> Penyisihan Round 1
            </a>
          </li>
          <li>
            <a
              href="https://portal.kokocoder.com/contests/logicode-2024-qualification-round-2"
              target="_blank"
              class="text-slate-600 text-sm sm:text-md md:text-lg underline"
            >
              <i class="bx bx-link-external"></i> Penyisihan Round 2
            </a>
          </li>
          <li>
            <a
              href="https://portal.kokocoder.com/contests/logicode-2024-final-round"
              target="_blank"
              class="text-slate-600 text-sm sm:text-md md:text-lg underline"
            >
              <i class="bx bx-link-external"></i> Final Round
            </a>
          </li>
        </ul>
      </div>
      <div
        class="flex flex-col border border-slate-200 shadow-md px-4 py-2 rounded-lg w-full"
      >
        <h3 class="text-orange-400 font-bold font-mono sm:text-lg md:text-xl">
          Logicode 2023
        </h3>
        <ul>
          <li>
            <a
              href="https://portal.kokocoder.com/contests/quiz/logicode-2023-penyisihan-round-1"
              target="_blank"
              class="text-slate-600 text-sm sm:text-md md:text-lg underline"
            >
              <i class="bx bx-link-external"></i> Penyisihan Round 1
            </a>
          </li>
          <li>
            <a
              href="https://portal.kokocoder.com/contests/logicode-2023-penyisihan-round-2"
              target="_blank"
              class="text-slate-600 text-sm sm:text-md md:text-lg underline"
            >
              <i class="bx bx-link-external"></i> Penyisihan Round 2
            </a>
          </li>
          <li>
            <a
              href="https://portal.kokocoder.com/contests/logicode-2023-final-round-2"
              target="_blank"
              class="text-slate-600 text-sm sm:text-md md:text-lg underline"
            >
              <i class="bx bx-link-external"></i> Final Round
            </a>
          </li>
        </ul>
      </div>

      <div
        class="flex flex-col border border-slate-200 shadow-md px-4 py-2 rounded-lg w-full"
      >
        <h3 class="text-orange-400 font-bold font-mono sm:text-lg md:text-xl">
          Logicode 2022
        </h3>
        <ul>
          <li>
            <a
              href="https://portal.kokocoder.com/contests/quiz/logicode-2022-round-1"
              target="_blank"
              class="text-slate-600 text-sm sm:text-md md:text-lg underline"
            >
              <i class="bx bx-link-external"></i> Round 1
            </a>
          </li>
          <li>
            <a
              href="https://portal.kokocoder.com/contests/logicode-2022-round-2"
              target="_blank"
              class="text-slate-600 text-sm sm:text-md md:text-lg underline"
            >
              <i class="bx bx-link-external"></i> Round 2
            </a>
          </li>
        </ul>
      </div>

      <button
        class="py-4 px-28 rounded-xl bg-slate-50 bg-opacity:50 cursor-pointer transition-all"
        @click="$emit('scrollToSection', 'contact')"
      >
        <span class="flex gap-2 text-lg font-bold">
          NEXT <i id="intro-next" class="bx bx-down-arrow-alt"></i>
        </span>
      </button>
    </div>
  </intersect>
</template>

<script>
import Intersect from "vue-intersect";

export default {
  components: {
    Intersect,
  },
  methods: {
    enterSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".problems-archive-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
    },
    leaveSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".problems-archive-title",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "-40px", duration: 1 }
        );
    },
  },
};
</script>
