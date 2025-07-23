<template>
  <div class="flex flex-col h-full min-h-screen relative">
    <div
      class="flex flex-col items-center gap-2 absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2"
    >
      <h1
        class="font-bold font-mono text-5xl sm:text-6xl md:text-7xl text-center typewriter-container"
      >
        <span id="typewriter-text" class="typewriter-text"></span>
        <span class="typewriter-cursor">|</span>
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
  mounted() {
    this.startTypewriter();
  },
  data() {
    return {
      hovering: false,
    };
  },
  methods: {
    startTypewriter() {
      if (process.browser) {
        const text = "LOGICODE 2025";
        const textElement = document.getElementById("typewriter-text");
        let index = 0;
        
        // Responsive timing based on screen size
        const getTypingSpeed = () => {
          if (window.innerWidth < 640) return 120; // sm screens - faster
          if (window.innerWidth < 768) return 140; // md screens - medium
          return 160; // lg screens - slower for dramatic effect
        };
        
        const typeChar = () => {
          if (index < text.length) {
            textElement.textContent += text.charAt(index);
            index++;
            setTimeout(typeChar, getTypingSpeed());
          }
        };
        
        setTimeout(typeChar, 500);
      }
    },
  },
};
</script>

<style lang="css" scoped>
.typewriter-container {
  display: inline-block;
}

.typewriter-text {
  display: inline-block;
}

.typewriter-cursor {
  display: inline-block;
  animation: blink 1s infinite;
  font-weight: normal;
  margin-left: 2px;
}

/* Responsive cursor adjustments */
@media (max-width: 640px) {
  .typewriter-cursor {
    margin-left: 1px;
    font-size: 0.9em;
  }
}

@media (min-width: 768px) {
  .typewriter-cursor {
    margin-left: 3px;
  }
}

@keyframes blink {
  0%, 50% {
    opacity: 1;
  }
  51%, 100% {
    opacity: 0;
  }
}
</style>
