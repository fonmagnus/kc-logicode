<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0.6]">
    <div
      id="contact"
      class="flex flex-col h-full min-h-screen justify-center items-center p-6 sm:px-24 md:px-48 lg:px-72 xl:px-96 gap-6 sm:gap-6 md:gap-12 relative overflow-hidden"
    >
      <div class="flex flex-col items-center justify-center gap-4 sm:gap-6">
        <div class="flex flex-col items-center justify-center gap-4">
          <h1
            class="opacity-0 contact-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
          >
            Mau tanya-tanya? 📱
          </h1>

          <p
            class="opacity-0 contact-description text-md text-center sm:text-xl md:text-2xl text-slate-600"
          >
            <span
              >Kalau kamu masih memiliki pertanyaan seputar Logicode 2023,
              jangan malu-malu ya buat hubungi tim admin Kokocoder melalui :
            </span>
          </p>
        </div>
      </div>

      <div class="flex flex-col gap-2">
        <a
          class="opacity-0 contact-card-1 font-bold sm:text-lg md:text-xl lg:text-2xl xl:text-3xl"
          href="https://www.instagram.com/kokocoder/?hl=en"
          target="_blank"
        >
          <div
            class="flex items-center gap-2 border-2 border-black px-8 py-4 rounded-lg hover:bg-gradient-to-r hover:from-purple-500 hover:via-pink-500 hover:to-yellow-500 transition-all cursor-pointer hover:text-white"
          >
            <i class="bx bxl-instagram text-2xl"></i>
            kokocoder
          </div>
        </a>
        <a
          class="opacity-0 contact-card-2 font-bold sm:text-lg md:text-xl lg:text-2xl xl:text-3xl"
          href="https://kokocoder.com"
          target="_blank"
        >
          <div
            class="flex items-center gap-2 border-2 border-black px-8 py-4 rounded-lg hover:bg-black transition-all cursor-pointer hover:text-white"
          >
            <i class="bx bx-globe text-2xl"></i>
            kokocoder.com
          </div>
        </a>

        <a
          class="opacity-0 contact-card-3 font-bold sm:text-lg md:text-xl lg:text-2xl xl:text-3xl"
          href="https://wa.link/haavs6"
          target="_blank"
        >
          <div
            class="flex items-center gap-2 border-2 border-black px-8 py-4 rounded-lg hover:bg-gradient-to-r hover:from-green-800 hover:to-green-600 transition-all cursor-pointer hover:text-white"
          >
            <i class="bx bxl-whatsapp text-2xl"></i>

            <div class="flex flex-col">
              0812-8281-9267
              <span class="text-base"> (Kak Abdul - Competition Head) </span>
            </div>
          </div>
        </a>
        <a
          class="opacity-0 contact-card-4 font-bold sm:text-lg md:text-xl lg:text-2xl xl:text-3xl"
          href="https://wa.link/qmlbj1"
          target="_blank"
        >
          <div
            class="flex items-center gap-2 border-2 border-black px-8 py-4 rounded-lg hover:bg-gradient-to-r hover:from-green-800 hover:to-green-600 transition-all cursor-pointer hover:text-white"
          >
            <i class="bx bxl-whatsapp text-2xl"></i>

            <div class="flex flex-col">
              0877-8585-7166
              <span class="text-base"> (Kak Monic - Public Relation) </span>
            </div>
          </div>
        </a>

        <a
          class="opacity-0 contact-card-5 font-bold sm:text-lg md:text-xl lg:text-2xl xl:text-3xl"
          href="https://wa.link/sg6dfw"
          target="_blank"
        >
          <div
            class="flex items-center gap-2 border-2 border-black px-8 py-4 rounded-lg hover:bg-gradient-to-r hover:from-green-800 hover:to-green-600 transition-all cursor-pointer hover:text-white"
          >
            <i class="bx bxl-whatsapp text-2xl"></i>

            <div class="flex flex-col">
              0858-1124-5759
              <span class="text-base"> (Kak Arnold - CEO Kokocoder) </span>
            </div>
          </div>
        </a>
      </div>

      <span class="absolute bottom-0 mb-24 text-sm text-slate-600">
        &copy;kokocoder 2023
      </span>
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
      this.$gsap.to("#contact-next", {
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

      document.getElementById("contact").appendChild(newDiv);

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
          ".contact-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-description",
          { opacity: 0, x: "40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-1",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 0.25 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-2",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 0.5 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-3",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 0.75 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-4",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-5",
          { opacity: 0, y: "40px" },
          { opacity: 1, y: "0px", duration: 1, delay: 1.25 }
        );
    },
    leaveSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-title",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "-40px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-description",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "40px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-1",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-2",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-3",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-4",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".contact-card-5",
          { opacity: 1, y: "0px", duration: 1 },
          { opacity: 0, y: "40px" }
        );
    },
  },
};
</script>

<style>
</style>
