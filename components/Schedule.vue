<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0.6]">
    <div
      id="schedule"
      class="flex flex-col h-full min-h-screen justify-center items-center p-6 sm:px-24 md:px-48 lg:px-72 xl:px-96 gap-6 sm:gap-6 md:gap-12 relative overflow-hidden"
    >
      <div class="flex flex-col items-center justify-center gap-4 sm:gap-6">
        <div class="flex flex-col items-center justify-center gap-4">
          <h1
            class="opacity-0 schedule-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
          >
            Tanggal Mainnya? 🤷‍♂️
          </h1>

          <p
            class="opacity-0 schedule-description text-md text-center sm:text-xl md:text-2xl text-slate-600"
          >
            <span
              >Akan ada 2 babak utama yaitu babak <b>Penyisihan</b> dan
              <b>Final</b>.
            </span>
            <span>Berikut jadwal pelaksanaannya</span>
          </p>
        </div>
        <div class="flex flex-col gap-4 sm:gap-4 md:gap-6 w-full">
          <div
            class="opacity-0 schedule-card-1 flex flex-col border border-slate-200 shadow-md px-4 py-2 rounded-lg w-full"
          >
            <h3
              class="text-orange-400 font-bold font-mono sm:text-lg md:text-xl"
            >
              Penyisihan
            </h3>
            <span class="text-slate-600 sm:text-lg md:text-xl"
              ><b>Sesi 1 - Logic</b></span
            >
            <span class="text-slate-600 text-sm sm:text-md md:text-lg"
              >🗓️ Sabtu, 9 Agustus 2025</span
            >
            <span class="text-slate-600 text-sm sm:text-md md:text-lg"
              >🕘 09.05 - 10.35</span
            >
          </div>
          <div
            class="opacity-0 schedule-card-2 flex flex-col border border-slate-200 shadow-md px-4 py-2 rounded-lg w-full"
          >
            <h3
              class="text-orange-400 font-bold font-mono sm:text-lg md:text-xl"
            >
              Penyisihan
            </h3>
            <span class="text-slate-600 sm:text-lg md:text-xl"
              ><b>Sesi 2 - Code</b></span
            >
            <span class="text-slate-600 text-sm sm:text-md md:text-lg"
              >🗓️ Sabtu, 9 Agustus 2025</span
            >
            <span class="text-slate-600 text-sm sm:text-md md:text-lg"
              >🕘 11.05 - 13.05</span
            >
          </div>
          <div
            class="opacity-0 schedule-card-3 flex flex-col border border-slate-200 shadow-md px-4 py-2 rounded-lg w-full"
          >
            <h3 class="text-blue-500 font-bold font-mono sm:text-lg md:text-xl">
              Final (Online)
            </h3>
            <span class="text-slate-600 sm:text-lg md:text-xl"
              ><b>Code</b></span
            >
            <span class="text-slate-600 text-sm sm:text-md md:text-lg"
              >🗓️ Sabtu, 20 September 2025</span
            >
            <span class="text-slate-600 text-sm sm:text-md md:text-lg"
              >🕘 08.35 - 13.35</span
            >
          </div>
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
            NEXT <i id="schedule-next" class="bx bx-down-arrow-alt"></i>
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
      this.$gsap.to("#schedule-next", {
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

      document.getElementById("schedule").appendChild(newDiv);

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
          ".schedule-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".schedule-description",
          { opacity: 0, x: "40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".schedule-card-1",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 0.25 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".schedule-card-2",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 0.5 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".schedule-card-3",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 0.75 }
        );
    },
    leaveSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".schedule-title",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "-40px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".schedule-description",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "40px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".schedule-card-1",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".schedule-card-2",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".schedule-card-3",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
    },
  },
};
</script>

<style></style>
