<template>
  <div class="flex flex-col h-full min-h-screen relative">
    <div
      class="flex flex-col items-center gap-2 absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"
    >
      <h1
        class="font-bold font-mono text-5xl sm:text-6xl md:text-7xl text-center"
      >
        LOGICODE 2024
      </h1>
      <h3 class="text-lg sm:text-xl md:text-2xl text-center">
        👩🏻‍💻 (by Kokocoder Group) 👨🏼‍💻
      </h3>
    </div>

    <button
      class="box mb-36 absolute bottom-0 left-1/2 -translate-x-1/2 p-4 border-2 border-black rounded-xl transition-all hover:bg-slate-100 cursor-pointer"
      @mouseover="hovering = true"
      @mouseleave="hovering = false"
      @click="$emit('scrollToSection', 'intro')"
    >
      <span class="text-xl text-center font-bold">
        START <span>{{ !hovering ? "😊" : "😄" }}</span>
        <i class="bx bx-down-arrow-alt"> </i
      ></span>
    </button>
  </div>
</template>

<script>
export default {
  mounted() {},
  data() {
    return {
      hovering: false,
    };
  },
  methods: {},
};
</script>

<style lang="css" scoped></style>
