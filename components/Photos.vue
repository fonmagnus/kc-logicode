<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0.6]">
    <div
      id="photos"
      class="flex flex-col h-full justify-center items-center p-6 gap-6 sm:px-24 md:px-48 lg:px-72 xl:px-96"
    >
      <h1
        class="opacity-0 photos-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
      >
        Foto-foto Logicode 2023
      </h1>

      <div id="gallery" class="m-auto grid lg:grid-cols-3 gap-6 lg:gap-1">
        <a
          v-for="(image, key) in imagesData"
          :key="key"
          :href="getUrl(image.fileName)"
          :data-pswp-width="image.width"
          :data-pswp-height="image.height"
          target="_blank"
          rel="noreferrer"
          class="aspect-square"
        >
          <img
            :src="getUrl(image.fileName)"
            alt=""
            class="w-full h-full object-cover"
          />
        </a>
      </div>

      <button
        class="py-4 px-28 rounded-xl bg-slate-50 bg-opacity:50 cursor-pointer transition-all"
        @click="$emit('scrollToSection', 'problems-archive')"
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
import PhotoSwipeLightbox from "photoswipe/dist/photoswipe-lightbox.esm";

export default {
  components: {
    Intersect,
  },
  data() {
    return {
      imagesData: [
        {
          fileName: "DSC05376.jpg",
          width: 1688,
          height: 2110,
        },
        {
          fileName: "DSC05254.jpg",
          width: 1688,
          height: 3000,
        },
        {
          fileName: "DSC05274.jpg",
          width: 3000,
          height: 1688,
        },
        {
          fileName: "DSC05200.jpg",
          width: 2623,
          height: 1476,
        },
        {
          fileName: "DSC05332.jpg",
          width: 3000,
          height: 1688,
        },
        {
          fileName: "DSC05307.jpg",
          width: 1688,
          height: 2110,
        },
        {
          fileName: "DSC05355.jpg",
          width: 2560,
          height: 1440,
        },
        {
          fileName: "DSC05249.jpg",
          width: 1688,
          height: 3000,
        },
        {
          fileName: "DSC05217.jpg",
          width: 1610,
          height: 2861,
        },
      ],
    };
  },
  methods: {
    getUrl(img) {
      if (!img) return "";
      return require(`~/assets/image/${img}`);
    },
    enterSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".photos-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
    },
    leaveSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".photos-title",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "-40px", duration: 1 }
        );
    },
  },
  mounted() {
    if (!this.lightbox) {
      this.lightbox = new PhotoSwipeLightbox({
        gallery: "#gallery",
        children: "a",
        pswpModule: () => import("photoswipe/dist/photoswipe.esm"),
      });
      this.lightbox.init();
    }
  },
  unmounted() {
    if (this.lightbox) {
      this.lightbox.destroy();
      this.lightbox = null;
    }
  },
};
</script>
