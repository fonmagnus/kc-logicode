<template>
  <div
    id="intro"
    class="flex flex-col h-full min-h-screen items-center justify-center p-12 gap-12 relative"
  >
    <div class="flex flex-col items-center justify-center min-h-[60vh] gap-12">
      <h1 class="text-6xl text-black font-mono font-extrabold text-center">
        Apa itu Logicode? 🤷‍♀️
      </h1>

      <p class="text-center text-2xl">
        <span class="text-slate-600 text-center"
          >Logicode adalah kompetisi reguler yang diadakan Kokocoder setiap
          tahunnya.</span
        >
        <br />
        <span class="text-slate-600 text-center"
          >Di kompetisi ini kamu akan bertanding dengan peserta lain di bidang
          <b>matematika</b> dan <b>coding</b>!</span
        >
      </p>
    </div>

    <div class="flex flex-col shrink gap-2">
      <button
        class="border-2 border-slate-500 py-4 px-32 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
        @click="spawnEmoji('😮')"
      >
        <span class="text-3xl">😮</span>
      </button>
      <button
        class="py-4 px-32 rounded-xl bg-slate-50 bg-opacity:50 cursor-pointer transition-all"
      >
        <span class="flex gap-2 text-lg font-bold">
          NEXT <i id="intro-next" class="bx bx-down-arrow-alt"></i>
        </span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
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
  },
};
</script>

<style>
</style>
