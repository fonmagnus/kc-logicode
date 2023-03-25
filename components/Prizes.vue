<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0.6]">
    <div
      id="prizes"
      class="flex flex-col h-full min-h-screen justify-center items-center p-6 sm:px-24 md:px-48 lg:px-72 xl:px-96 gap-6 sm:gap-6 md:gap-12 relative overflow-hidden"
    >
      <div class="flex flex-col items-center justify-center gap-4 sm:gap-6">
        <div class="flex flex-col items-center justify-center gap-4">
          <h1
            class="opacity-0 prizes-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
          >
            Ada Hadiahnya gak? 🎁😲
          </h1>

          <p
            class="opacity-0 prizes-description text-md text-center sm:text-xl md:text-2xl text-slate-600"
          >
            <span>Tentu ada dong! </span>
            <span>Berikut daftar hadiah bagi para pemenangnya</span>
          </p>
        </div>
      </div>

      <div class="flex flex-col sm:gap-4 md:gap-6 w-full">
        <div
          class="flex prizes-card-1 justify-between items-center gap-4 border border-slate-200 shadow-md px-6 py-4 rounded-lg w-full"
        >
          <div class="opacity-0 flex flex-col">
            <h3 class="font-bold font-mono sm:text-lg md:text-xl">
              Juara 1 - Absolute
            </h3>
            <span
              class="text-orange-500 text-2xl sm:text-4xl md:text-5xl font-extrabold"
              >Rp. 2.000.000</span
            >
          </div>

          <span class="text-4xl sm:text-5xl md:text-6xl"> 💎 </span>
        </div>

        <div
          class="flex prizes-card-2 justify-between items-center gap-4 border border-slate-200 shadow-md px-6 py-4 rounded-lg w-full"
        >
          <div class="opacity-0 flex flex-col">
            <h3 class="font-bold font-mono sm:text-lg md:text-xl">
              Juara 2-3 - Gold
            </h3>
            <span
              class="text-orange-500 text-2xl sm:text-4xl md:text-5xl font-extrabold"
              >Rp. 1.000.000</span
            >
          </div>

          <span class="text-4xl sm:text-5xl md:text-6xl"> 🥇 </span>
        </div>

        <div
          class="flex prizes-card-3 justify-between items-center gap-4 border border-slate-200 shadow-md px-6 py-4 rounded-lg w-full"
        >
          <div class="opacity-0 flex flex-col">
            <h3 class="font-bold font-mono sm:text-lg md:text-xl">
              Juara 4-6 Silver
            </h3>
            <span
              class="text-orange-500 text-2xl sm:text-4xl md:text-5xl font-extrabold"
              >Rp. 750.000</span
            >
          </div>

          <span class="text-4xl sm:text-5xl md:text-6xl"> 🥈 </span>
        </div>

        <div
          class="flex prizes-card-4 justify-between items-center gap-4 border border-slate-200 shadow-md px-6 py-4 rounded-lg w-full"
        >
          <div class="opacity-0 flex flex-col">
            <h3 class="font-bold font-mono sm:text-lg md:text-xl">
              Juara 7-10 Bronze
            </h3>
            <span
              class="text-orange-500 text-2xl sm:text-4xl md:text-5xl font-extrabold"
              >Rp. 500.000</span
            >
          </div>

          <span class="text-4xl sm:text-5xl md:text-6xl"> 🥉 </span>
        </div>

        <div
          class="flex prizes-card-5 justify-between items-center gap-4 border border-slate-200 shadow-md px-6 py-4 rounded-lg w-full"
        >
          <div class="opacity-0 flex flex-col">
            <h3 class="font-bold font-mono sm:text-lg md:text-xl">
              Seluruh Peserta
            </h3>
            <span
              class="text-orange-500 text-xl sm:text-2xl md:text-3xl font-extrabold"
              >Rp. 100.000
            </span>
            <span class="text-sm font-medium text-orange-500"
              >Untuk setiap soal yang Accepted pada sesi 2 babak
              penyisihan</span
            >
            <span class="text-black text-md font-medium"
              >dalam bentuk Voucher belajar di Kokocoder</span
            >
          </div>

          <span class="text-2xl sm:text-3xl md:text-4xl"> 💌 </span>
        </div>
      </div>

      <div class="flex flex-col items-center gap-2">
        <!-- <div class="flex gap-2">
          <button
            class="border-2 border-slate-500 py-2 px-14 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
            @click="spawnEmoji('❤️')"
          >
            <span class="text-xl">❤️</span>
          </button>
          <button
            class="border-2 border-slate-500 py-2 px-14 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
            @click="spawnEmoji('🤩')"
          >
            <span class="text-xl">🤩</span>
          </button>
        </div> -->
        <button
          class="py-4 px-28 rounded-xl bg-slate-50 bg-opacity:50 cursor-pointer transition-all"
          @click="$emit('scrollToSection', 'prizes')"
        >
          <span class="flex gap-2 text-lg font-bold">
            NEXT <i id="prizes-next" class="bx bx-down-arrow-alt"></i>
          </span>
        </button>
      </div>
    </div>
  </intersect>
</template>

<script>
import Intersect from "vue-intersect";
export default {
  components: {
    Intersect,
  },
  mounted() {
    this.animateNextArrow();
  },
  methods: {
    animateNextArrow() {
      this.$gsap.to("#prizes-next", {
        yoyo: true,
        repeat: -1,
        y: "10px",
        duration: 0.4,
        ease: "power1.inOut",
      });
    },
    spawnEmoji(emo) {
      const { x, y } = this.getRandomPosition();
      const newDiv = document.createElement("div");
      newDiv.innerHTML = emo;
      newDiv.style.position = "absolute";
      newDiv.style.top = `${y}%`;
      newDiv.style.left = `${x}%`;
      newDiv.style.overflow = "hidden";
      // newDiv.style.zIndex = -1;
      newDiv.style.userSelect = "none";
      newDiv.style.transform = "translate(-50%, -50%)";

      document.getElementById("prizes").appendChild(newDiv);

      this.$gsap.timeline().fromTo(
        newDiv,
        { fontSize: "24px", opacity: 1, top: `${y}%` },
        {
          fontSize: "144px",
          opacity: 0,
          display: "none",
          duration: 1.5,
          top: `${y - 100}%`,
        }
      );
    },
    getRandomPosition() {
      const x = Math.random() * 100;
      const y = Math.random() * 20 + 80;
      return { x, y };
    },

    enterSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-description",
          { opacity: 0, x: "40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-card-1",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 0.25 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-card-2",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 0.5 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-card-3",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 0.75 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-card-4",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-card-5",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 1.25 }
        );
    },
    leaveSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-title",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "-40px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-description",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "40px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-card-1",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-card-2",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-card-3",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".prizes-card-4",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
    },
  },
};
</script>

<style>
</style>
