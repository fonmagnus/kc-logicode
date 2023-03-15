<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0.6]">
    <div
      id="registration"
      class="flex flex-col h-full min-h-screen justify-center items-center p-6 sm:px-24 md:px-48 lg:px-72 xl:px-96 gap-6 sm:gap-6 md:gap-12 relative overflow-hidden"
    >
      <div class="flex flex-col items-center justify-center gap-4 sm:gap-6">
        <div class="flex flex-col items-center justify-center gap-4">
          <h1
            class="opacity-0 registration-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
          >
            {{
              hasSubmittedForm
                ? "Pendaftaran Berhasil! 🥳 ✅"
                : "Daftar Yuk! 👇"
            }}
          </h1>

          <p
            class="opacity-0 registration-description text-md text-center sm:text-xl md:text-2xl text-slate-600"
          >
            <span v-if="!hasSubmittedForm"
              >Tertarik bertanding dalam kompetisi ini? Ayo daftarkan dirimu
              segera!</span
            >
            <span v-else
              >Kamu sudah terdaftar sebagai peserta Logicode 2023! Tunggu admin
              untuk menginvite mu ke dalam grup Whatsapp yaa. Sampai jumpa di
              Logicode 2023</span
            >
          </p>
        </div>
      </div>

      <div v-if="!hasSubmittedForm" class="flex flex-col gap-4 w-full">
        <Input
          label="Email"
          v-model="form.email"
          required
          :errors="errors.email"
        />
        <Input
          label="Nama Lengkap"
          v-model="form.name"
          required
          :errors="errors.name"
        />
        <Input
          label="Nomor Handphone"
          v-model="form.phone"
          required
          :errors="errors.phone"
        />
        <Input
          label="Sekolah"
          v-model="form.school"
          required
          :errors="errors.school"
        />
        <Choices
          label="Kelas"
          v-model="form.grade"
          required
          :errors="errors.grade"
          :choices="gradeOptions"
        />
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
          v-if="!hasSubmittedForm"
          class="py-4 px-28 mt-12 rounded-xl bg-transparent border-2 border-black bg-opacity:50 cursor-pointer transition-all hover:bg-black hover:text-white"
          @click="submitForm"
        >
          <span class="flex gap-2 text-lg font-bold"> DAFTAR </span>
        </button>
        <button
          v-else
          class="py-4 px-28 rounded-xl bg-slate-50 bg-opacity:50 cursor-pointer transition-all"
          @click="$emit('scrollToSection', 'contact')"
        >
          <span class="flex gap-2 text-lg font-bold">
            NEXT <i id="registration-next" class="bx bx-down-arrow-alt"></i>
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
  data() {
    return {
      form: {
        email: "",
        name: "",
        phone: "",
        school: "",
        grade: "",
      },
      hasFilledForm: {
        email: false,
        name: false,
        phone: false,
        school: false,
        grade: false,
      },
      errors: {
        email: [],
        name: [],
        phone: [],
        school: [],
        grade: [],
      },
      gradeOptions: [
        { label: 7, value: 7 },
        { label: 8, value: 8 },
        { label: 9, value: 9 },
        { label: 10, value: 10 },
        { label: 11, value: 11 },
      ],
      hasSubmittedForm: false,
    };
  },
  mounted() {
    this.animateNextArrow();
  },
  watch: {
    "form.email": {
      handler(val) {
        if (!val && !this.errors.email.includes("Email harus diisi")) {
          this.errors.email.push("Email harus diisi");
          return;
        }

        if (val)
          this.errors.email = this.errors.email.filter(
            (a) => a !== "Email harus diisi"
          );

        this.hasFilledForm.email = true;
        if (
          !this.validateEmail(val) &&
          !this.errors.email.includes("Format email tidak sesuai")
        ) {
          this.errors.email.push("Format email tidak sesuai");
          return;
        }

        if (this.validateEmail(val)) {
          this.errors.email = [];
        }
      },
    },
    "form.name": {
      handler(val) {
        if (val) {
          this.hasFilledForm.name = true;
          this.errors.name = [];
          return;
        }
        if (this.hasFilledForm.name)
          this.errors.name.push("Nama Lengkap harus diisi");
      },
    },
    "form.phone": {
      handler(val) {
        if (val) {
          this.errors.phone = [];
          this.hasFilledForm.phone = true;
          return;
        }
        if (this.hasFilledForm.phone)
          this.errors.phone.push("Nomor Handphone harus diisi");
      },
    },
    "form.school": {
      handler(val) {
        if (val) {
          this.errors.school = [];
          this.hasFilledForm.school = true;
          return;
        }
        if (this.hasFilledForm.school)
          this.errors.school.push("Sekolah harus diisi");
      },
    },
    "form.grade": {
      handler(val) {
        if (val) {
          this.errors.grade = [];
          this.hasFilledForm.grade = true;
          return;
        }
        if (this.hasFilledForm.grade)
          this.errors.grade.push("Kelas harus diisi");
      },
    },
  },
  methods: {
    animateNextArrow() {
      this.$gsap.to("#registration-next", {
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

      document.getElementById("registration").appendChild(newDiv);

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
          ".registration-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".registration-description",
          { opacity: 0, x: "40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
    },
    leaveSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".registration-title",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "-40px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".registration-description",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "40px", duration: 1 }
        );
    },

    validateEmail(email) {
      return String(email)
        .toLowerCase()
        .match(
          /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
        );
    },

    doValidation() {
      if (
        !this.form.email.length &&
        !this.errors.email.includes("Email harus diisi")
      )
        this.errors.email.push("Email harus diisi");
      if (
        !this.form.name.length &&
        !this.errors.name.includes("Nama lengkap harus diisi")
      )
        this.errors.name.push("Nama lengkap harus diisi");
      if (
        !this.form.phone.length &&
        !this.errors.phone.includes("Nomor handphone harus diisi")
      )
        this.errors.phone.push("Nomor handphone harus diisi");
      if (
        !this.form.school.length &&
        !this.errors.school.includes("Sekolah harus diisi")
      )
        this.errors.school.push("Sekolah harus diisi");
      if (!this.form.grade && !this.errors.grade.includes("Kelas harus diisi"))
        this.errors.grade.push("Kelas harus diisi");
      if (
        !this.validateEmail(this.form.email) &&
        !this.errors.email.includes("Format email tidak sesuai")
      )
        this.errors.email.push("Format email tidak sesuai");
    },

    submitForm() {
      this.doValidation();
      if (
        this.errors.email.length ||
        this.errors.name.length ||
        this.errors.phone.length ||
        this.errors.school.length ||
        this.errors.grade.length
      )
        return;

      this.hasSubmittedForm = true;
    },
  },
};
</script>

<style>
</style>
