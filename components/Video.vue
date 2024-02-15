<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0.6]">
    <div
      id="video"
      class="flex flex-col h-full justify-center items-center p-6 sm:px-24 md:px-48 lg:px-72 xl:px-96 gap-6"
    >
      <h1
        class="opacity-0 video-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
      >
        Video Logicode 2023
      </h1>

      <iframe
        src="https://drive.google.com/file/d/1jn2fPUJ8cJwtizWoVE3xyJu5g6r-ezOs/preview"
        width="100%"
        height="480"
        allow="autoplay"
      ></iframe>

      <button
        class="py-4 px-28 rounded-xl bg-slate-50 bg-opacity:50 cursor-pointer transition-all"
        @click="$emit('scrollToSection', 'schedule')"
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
          ".video-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
    },
    leaveSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".video-title",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "-40px", duration: 1 }
        );
    },
  },
};
</script>
