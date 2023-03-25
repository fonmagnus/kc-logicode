<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0.6]">
    <div
      id="testimonials"
      class="flex flex-col h-full min-h-screen justify-center items-center p-6 py-8 sm:px-24 md:px-48 lg:px-72 xl:px-96 gap-6 relative overflow-hidden"
    >
      <div class="flex flex-col justify-center items-center gap-4 w-full">
        <h1
          class="opacity-0 testimonials-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
        >
          Kata Mereka 💬
        </h1>

        <p
          class="testimonials-description text-center text-sm sm:text-md md:text-lg"
        >
          <span class="text-slate-600 text-center"
            >Penasaran kayak gimana kompetisi Logicode? Ini cerita peserta yang
            mengikuti Logicode 2022 lalu!
          </span>
        </p>
      </div>

      <div
        class="flex flex-col grow relative max-h-[66vh] lg:max-h-[70vh] h-auto w-full"
        :class="[
          {
            'overflow-scroll': !activeTestimonial.name,
            'overflow-hidden': activeTestimonial.name,
          },
        ]"
      >
        <template v-if="!activeTestimonial.name">
          <div
            class="flex items-center gap-4 border-b border-b-slate-300 pr-3 py-2 hover:bg-slate-100 transition-all cursor-pointer"
            v-for="(testimonial, i) in testimonials"
            :key="i"
            @click="showTestimonial(testimonial)"
          >
            <div class="flex gap-2 grow">
              <div class="w-14 h-14 rounded-full">
                <img
                  class="w-14 h-14 sm:w-14 sm:h-14 object-cover rounded-full"
                  :src="getUrl(testimonial.photo)"
                  alt=""
                />
              </div>
              <div class="flex flex-col">
                <span class="font-semibold">{{ testimonial.name }}</span>
                <span
                  class="text-slate-500 truncate text-sm max-w-[60vw] sm:max-w-[50vw] md:max-w-[40vw] lg:max-w-[30vw]"
                  >{{ testimonial.message }}</span
                >
              </div>
            </div>
            <div class="flex flex-col items-end justify-center gap-1 shrink">
              <span class="text-green-500 text-sm">20:22</span>
              <div
                class="rounded-full flex justify-center items-center w-5 h-5 sm:w-6 sm:h-6 text-center bg-green-500 text-white text-sm"
              >
                1
              </div>
            </div>
          </div>
        </template>

        <div
          class="absolute opacity-0 -z-10 testimonial-dialog top-0 flex flex-col w-full"
          :class="[
            {
              'h-full': activeTestimonial.name,
              'h-0': !activeTestimonial.name,
            },
          ]"
        >
          <div class="flex w-full bg-green-900 py-2 px-2 text-white gap-1">
            <div
              class="flex items-center cursor-pointer"
              @click="hideTestimonial"
            >
              <i class="bx bx-left-arrow-alt text-white text-2xl"></i>
            </div>
            <div class="flex">
              <img
                class="w-10 h-10 object-cover rounded-full"
                :src="getUrl(activeTestimonial.photo)"
                alt=""
              />
            </div>
            <div class="flex flex-col h-full">
              <span class="font-semibold">{{ activeTestimonial.name }}</span>
              <span class="text-xs truncate">{{
                activeTestimonial.title
              }}</span>
            </div>
          </div>
          <div
            class="flex flex-col h-full p-4 overflow-scroll bg-orange-100 relative"
          >
            <div class="bg-white px-4 py-2 rounded-lg">
              <span>{{ activeTestimonial.message }}</span>
            </div>

            <div
              class="flex gap-2 justify-end absolute bottom-0 right-0 m-4 overflow-scroll w-fit"
            >
              <button
                class="bg-white py-2 px-8 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
                @click="spawnEmoji('❤️')"
              >
                <span class="text-xl">❤️</span>
              </button>
              <button
                class="bg-white py-2 px-8 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
                @click="spawnEmoji('🤩')"
              >
                <span class="text-xl">🤩</span>
              </button>
              <button
                class="bg-white py-2 px-8 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
                @click="spawnEmoji('👍')"
              >
                <span class="text-xl">👍</span>
              </button>
              <button
                class="bg-white py-2 px-8 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
                @click="spawnEmoji('🔥')"
              >
                <span class="text-xl">🔥</span>
              </button>
            </div>
          </div>
        </div>
      </div>

      <div class="flex flex-col shrink gap-2">
        <button
          class="py-4 px-28 rounded-xl bg-slate-50 bg-opacity:50 cursor-pointer transition-all"
          @click="$emit('scrollToSection', 'registration')"
        >
          <span class="flex gap-2 text-lg font-bold">
            NEXT <i id="testimonials-next" class="bx bx-down-arrow-alt"></i>
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
  data() {
    return {
      activeTestimonial: {},
      testimonials: [
        {
          name: "Benedict Presley",
          photo: "presley.jpg",
          message:
            "Menurut saya, tingkat kesulitan soalnya balanced. Soal - soalnya juga edukatif dan menyangkut banyak topik. Semangat buat para peserta Logicode 2023. Jangan lupa untuk have fun!",
          title: "Gold Medalist OSN Informatika 2022",
        },
        {
          name: "Nathan Keith",
          photo: "nathan-keith.jpg",
          message:
            "Lombanya secara keseluruhan telah disiapkan dengan baik, dan hal tersebut terlihat dari kualitas soal-soal yang diberikan pada ronde logika dan programming. Soal-soalnya sangat menantang, unik, dan original karena dibuat dari tim medallist OSN dan IOI yang sangat kece. Overall, kalian wajib ikut Logicode jika ingin menantang diri kalian bersama dengan kompetitor” imba lainnya 😎",
          title: "Gold Medalist OSN Informatika 2022",
        },
        {
          name: "Roberto Eugenio ",
          photo: "roberto.jpeg",
          message:
            "Bagiku mengikuti Logicode itu adalah salah satu pengalaman pertama mengikuti lomba informatika selain OSN. Sewaktu mengikuti Logicode itu seru, karena tidak seperti lomba-lomba lainnya yang sifatnya sangat formal. Panitia-panitia Logicode itu juga sangat ramah dan friendly. Soal-soalnya juga berkualitas, dan bervariasi kesulitannya dari yang mudah sampai sulit, sehingga aku juga belajar banyak hal baru dari sesi editorial/pembahasan soal-soal Logicode. Pengalamanku yang paling terkesan sewaktu ikut Logicode adalah momen greget ketika code yang harusnya AC malah jadi WA gara-gara kurang satu tanda '=' dan masih teringat sampai sekarang. Overall, it was a fun experience.",
          title: "Gold Medalist OSN Informatika 2022",
        },
        {
          name: "Daffa Rayhan Ananda",
          photo: "daffa.jpg",
          message:
            "Soal-soal logicode sangatlah berkualitas dan menantang. Hal yang saya suka adalah setelah kontes, soal-soalnya dibahas oleh para problemsetter. Anda pasti tidak akan menyesal mengikuti logicode.",
          title: "Silver Medalist OSN Informatika 2022",
        },
        {
          name: "Maydeline Davidson",
          photo: "maydeline.jpg",
          message:
            "Logicode 2022 seruu banget! Selain soal”nya yang original dan berkualitas, ada sesi” pembahasan bareng tim SC yang kerenn”. Dari lomba ini, aku ketemu banyak temen baru yang saling support untuk belajar bareng di dunia cp ini. Definitely recommended buat kalian ikutin terutama yang mau belajar Competitive Programming lebih lagi! 🫶",
          title: "Silver Medalist OSN Informatika 2022",
        },
        {
          name: "Joceline Araki",
          photo: "joceline.jpg",
          message:
            "Pengalaman ikut Logicode keren banget! Soal-soalnya asik, kreatif, dan berkualitas banget. Kakak-kakak SC (scientific commitee)-nya sendiri juga gercep dan membantu banget kalau ada pertanyaan atau kesulitan selama kompetisi. 10/10",
          title: "Silver Medalist OSN Informatika 2022",
        },
        {
          name: "Galih Nur Rizqy",
          photo: "galih.jpg",
          message:
            "Soal-soal Logicode beda banget dibanding soal-soal tryout OSK yang lain, unik dan berkualitas karena dibuat oleh troops sama coach KC sendiri, jadi gabakal pernah nemuin tu soal logicode di soal tryout yang lain, bahkan soal logicode lebih susah dibanding soal OSK sendiri!",
          title: "Silver Medalist OSN Informatika 2022",
        },
      ],
    };
  },
  methods: {
    animateNextArrow() {
      this.$gsap.to("#testimonials-next", {
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

      document
        .getElementsByClassName("testimonial-dialog")[0]
        .appendChild(newDiv);

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
          ".testimonials-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
    },
    leaveSection() {},

    getUrl(img) {
      if (!img) return "";
      return require(`~/assets/image/${img}`);
    },
    showTestimonial(testimonial) {
      this.activeTestimonial = testimonial;

      this.$gsap.timeline().fromTo(
        ".testimonial-dialog",
        {
          top: "100%",
          zIndex: -10,
          opacity: 0,
          display: "none",
          height: "0",
        },
        {
          top: "0%",
          zIndex: 10,
          opacity: 1,
          display: "flex",
          height: "100%",
          duration: 0.05,
        }
      );
    },
    hideTestimonial() {
      this.activeTestimonial = {};

      this.$gsap.timeline().fromTo(
        ".testimonial-dialog",
        { top: "0%", opacity: 1, zIndex: 10, height: "100%", display: "flex" },
        {
          top: "100%",
          opacity: 0,
          zIndex: -10,
          height: "0",
          display: "none",
          duration: 0.05,
        }
      );
    },
  },
};
</script>

<style>
</style>
