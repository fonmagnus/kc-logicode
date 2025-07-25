<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0.6]">
    <div
      id="intro"
      class="flex flex-col h-full min-h-screen items-center justify-center p-6 sm:px-24 md:px-48 lg:px-72 xl:px-96 gap-6 relative overflow-hidden"
    >
      <div
        class="flex flex-col items-center justify-center min-h-[60vh] gap-12 w-full"
      >
        <h1
          class="opacity-0 intro-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
        >
          Apa itu Logicode? 🤷‍♀️
        </h1>

        <p class="intro-description text-center text-lg sm:text-xl md:text-2xl">
          <span class="text-slate-600 text-center"
            >Logicode adalah kompetisi reguler yang diadakan Kokocoder setiap
            tahunnya untuk kamu yang masih duduk di
            <b>kelas 7 SMP - 12 SMA</b></span
          >
          <br />
          <br />
          <span class="text-slate-600 text-center"
            >Di kompetisi ini kamu akan bertanding dengan peserta lain di bidang
            <b>matematika </b> dan <b>coding</b>!</span
          >
        </p>
      </div>

      <div class="flex flex-col shrink gap-2">
        <div class="flex gap-4">
          <button
            class="border-2 border-slate-500 py-2 px-14 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
            @click="spawnEmoji('🔥')"
          >
            <span class="text-xl">🔥</span>
          </button>
          <button
            class="border-2 border-slate-500 py-2 px-14 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
            @click="spawnEmoji('😍')"
          >
            <span class="text-xl">😍</span>
          </button>
        </div>
        <button
          class="py-4 px-28 rounded-xl bg-slate-50 bg-opacity:50 cursor-pointer transition-all"
          @click="$emit('scrollToSection', 'video')"
        >
          <span class="flex gap-2 text-lg font-bold">
            NEXT <i id="intro-next" class="bx bx-down-arrow-alt"></i>
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
      this.$gsap.to("#intro-next", {
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

      document.getElementById("intro").appendChild(newDiv);

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
          ".intro-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".intro-description",
          { opacity: 0, x: "40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
    },
    leaveSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".intro-title",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "-40px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".intro-description",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "40px", duration: 1 }
        );
    },
  },
};
</script>

<style></style>
