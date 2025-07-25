<template>
  <intersect @enter="enterSection" @leave="leaveSection" :threshold="[0]">
    <div
      id="rules"
      class="flex flex-col h-full min-h-screen justify-center items-center p-6 sm:px-24 md:px-48 lg:px-72 xl:px-96 gap-6 sm:gap-6 md:gap-12 relative overflow-hidden"
    >
      <h1
        class="opacity-0 rules-title text-4xl sm:text-5xl md:text-6xl text-black font-mono font-extrabold text-center"
      >
        Rules 📜
      </h1>
      <div
        class="flex flex-col grow overflow-scroll relative"
        :class="[
          {
            'max-h-[66vh] lg:max-h-[70vh] h-full': !expanded,
          },
        ]"
      >
        <div
          class="opacity-0 rules-description flex flex-col justify-center gap-4"
        >
          <span class="font-bold text-slate-500 sm:text-lg md:text-xl">
            General Rules
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            1) Peserta merupakan siswa kelas
            <b>7 SMP - 12 SMA</b> dari seluruh Indonesia</span
          >

          <span class="text-slate-500 sm:text-lg md:text-xl">
            2) Peserta Belum pernah memenangkan medali OSN Informatika</span
          >

          <span class="text-slate-500 sm:text-lg md:text-xl">
            3) Kompetisi dapat diikuti secara <b>GRATIS</b> (tidak dikenakan biaya pendaftaran)</span
          >

          <span class="text-slate-500 sm:text-lg md:text-xl">
            4) Hadiah Pemenang :
            <br />
            <ul>
              <li>
                • <b>Juara 1</b> (Absolute Winner 👑) : Uang tunai senilai
                <b>Rp. 2.000.000</b>
              </li>
              <li>
                • <b>Juara 2-3</b> (Gold Medalist 🥇): Uang tunai senilai
                <b>Rp. 1.000.000</b>
              </li>
              <li>
                • <b>Juara 4-6</b> (Silver Medalist 🥈): Uang tunai senilai
                <b>Rp. 750.000</b>
              </li>
              <li>
                • <b>Juara 7-10</b> (Bronze Medalist 🥉): Uang tunai senilai
                <b>Rp. 500.000</b>
              </li>
              <!-- <li>
                • <b>Seluruh Peserta : </b> Voucher Kokocoder senilai
                <b>Rp. 100.000</b> untuk setiap soal "Accepted" pada sesi 2
                (code) babak Penyisihan
              </li> -->
            </ul>
          </span>

          <div class="border border-slate-400 my-2"></div>
          <span class="font-bold text-slate-500 sm:text-lg md:text-xl">
            Babak Penyisihan
          </span>

          <span class="text-slate-500 sm:text-lg md:text-xl">
            1) Babak Penyisihan terdiri dari 2 buah sesi yaitu sesi Logic dan
            sesi Code
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            2) <b>Sesi Logic</b>
            <br />
            <ol>
              <li>
                &nbsp; a. Dilaksanakan pada hari
                <b>Sabtu, 16 Agustus 2025 jam 09.05 - 10.35 WIB</b>
              </li>
              <li>
                &nbsp; b. Sesi ini terdiri dari <b>20 soal</b> logika,
                analitika, matematika, dan membaca kode
              </li>
              <li>&nbsp; c. Waktu untuk pengerjaan sesi adalah 90 menit</li>
              <li>&nbsp; d. Sesi ini dilaksanakan secara online</li>
              <li>
                &nbsp; e. Selama pelaksanaan, peserta DILARANG untuk :
                <br />
                <ul>
                  <li>&nbsp; &nbsp; • <b>Menggunakan kakas AI (Artificial Intelligence) atau LLM (Large Language Model)</b></li>
                  <li>&nbsp; &nbsp; • Bekerja sama dengan peserta lainnya</li>
                  <li>&nbsp; &nbsp; • Membuka Google / Browsing</li>
                  <li>&nbsp; &nbsp; • Menggunakan kalkulator digital</li>
                  <li>&nbsp; &nbsp; • Mengganti window / tab</li>
                  <li>&nbsp; &nbsp; • Membuat program</li>
                </ul>
              </li>
              <li>
                &nbsp; f. Peserta DIPERBOLEHKAN untuk:
                <br />
                <ul>
                  <li>
                    &nbsp; &nbsp; • Menggunakan kalkulator yang tersedia pada
                    platform
                  </li>
                  <li>&nbsp; &nbsp; • Menggunakan kalkulator fisik</li>
                  <li>&nbsp; &nbsp; • Menggunakan kertas coret-coretan</li>
                </ul>
              </li>
              <li>
                &nbsp; g. Penilaian untuk setiap jawaban pada sesi ini adalah
                sebagai berikut :

                <br />
                <ul>
                  <li>
                    &nbsp; &nbsp; • Jawaban <b>BENAR</b> mendapatkan nilai
                    <b>6 point</b>
                  </li>
                  <li>
                    &nbsp; &nbsp; • Jawaban <b>SALAH</b> mendapatkan nilai
                    <b>-2 point</b>
                  </li>
                  <li>
                    &nbsp; &nbsp; • Jawaban <b>KOSONG</b> mendapatkan nilai
                    <b>0 point</b>
                  </li>
                </ul>
              </li>
            </ol>
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            3) <b>Sesi Code</b>
            <br />
            <ol>
              <li>
                &nbsp; a. Dilaksanakan pada hari
                <b>Sabtu, 16 Agustus 2025 jam 11.05 - 13.05 WIB</b>
              </li>
              <li>
                &nbsp; b. Sesi ini terdiri dari <b>6-7 soal</b> pemrograman
                dengan tingkat kesulitan mudah-menengah
              </li>
              <li>&nbsp; c. Waktu untuk pengerjaan sesi adalah 120 menit</li>
              <li>&nbsp; d. Sesi ini dilaksanakan secara online</li>
              <li>
                &nbsp; e. Selama pelaksanaan, peserta DILARANG untuk :
                <br />
                <ul>
                  <li>&nbsp; &nbsp; • Bekerja sama dengan peserta lainnya</li>
                  <li>&nbsp; &nbsp; • Membuka Google / Browsing</li>
                </ul>
              </li>
              <li>
                &nbsp; f. Peserta DIPERBOLEHKAN untuk:
                <br />
                <ul>
                  <li>
                    &nbsp; &nbsp; • Menggunakan text editor (IDE) sendiri untuk
                    mengetik program
                  </li>
                  <li>&nbsp; &nbsp; • Menggunakan pre-written template code</li>
                  <li>&nbsp; &nbsp; • Menggunakan kertas coret-coretan</li>
                </ul>
              </li>
              <li>
                &nbsp; g. Penilaian untuk setiap jawaban pada sesi ini adalah
                sebagai berikut :

                <br />
                <ul>
                  <li>
                    Setiap soal memiliki nilai maksimal <b>100 point</b>
                  </li>
                  <li>
                    Total poin peserta untuk satu soal adalah jumlah poin untuk setiap subsoal yang
                    berhasil diselesaikan.
                  </li>
                </ul>
              </li>
            </ol>
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            4) <b>30 peserta*</b> dengan total nilai tertinggi yang diperoleh
            dari kedua sesi pada babak penyisihan akan
            <b>terkualifikasi ke babak final</b>. Peserta dengan perolehan nilai
            yang sama akan memperoleh peringkat yang sama.
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            5) Terdapat <i>online proctoring</i> pada babak penyisihan. Artinya
            pengerjaan soal akan diawasi secara online oleh panitia
          </span>
          <span class="text-slate-500 text-xs sm:text-base md:text-lg">
            *) Jumlah masih bersifat tentatif dan dapat berubah sewaktu-waktu.
          </span>

          <div class="border border-slate-400 my-2"></div>
          <span class="font-bold text-slate-500 sm:text-lg md:text-xl">
            Babak Final
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            1) Pelaksanaan babak final akan dilaksanakan secara
            <i>online</i> (daring). Adapun info lebih lanjut akan diumumkan setelah finalis terpilih.
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            2) Dilaksanakan pada hari
            <b>Sabtu, 20 September 2025 jam 08.35 - 13.35 WIB</b>
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            3) Sesi ini terdiri dari <b>8 soal</b> pemrograman dengan tingkat
            kesulitan mudah-sulit
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            4) Waktu untuk pengerjaan sesi adalah 300 menit
          </span>

          <span class="text-slate-500 sm:text-lg md:text-xl">
            5) Soal soal menggunakan tipe <b>IOI-style</b> dimana perolehan poin
            untuk setiap soal dapat bernilai parsial dari
            <b>0 s.d. 100 point</b>
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            6) Selama pelaksanaan, peserta DILARANG untuk :
            <br />
            <ul>
              <li>&nbsp; &nbsp; • <b>Menggunakan kakas AI (Artificial Intelligence) atau LLM (Large Language Model)</b></li>
              <li>&nbsp; &nbsp; • Bekerja sama dengan peserta lainnya</li>
              <li>&nbsp; &nbsp; • Membuka Google / Browsing</li>
            </ul>
          </span>

          <span class="text-slate-500 sm:text-lg md:text-xl">
            7) Peserta DIPERBOLEHKAN untuk:
            <br />
            <ul>
              <li>
                &nbsp; &nbsp; • Menggunakan text editor (IDE) sendiri untuk
                mengetik program
              </li>
              <li>&nbsp; &nbsp; • Menggunakan pre-written template code</li>
              <li>&nbsp; &nbsp; • Menggunakan kertas coret-coretan</li>
            </ul>
          </span>

          <span class="text-slate-500 sm:text-lg md:text-xl">
            8) Pemenang ditentukan berdasarkan perolehan total poin yang
            didapatkan di babak final. 10 Peserta dengan total poin tertinggi
            berhak mendapatkan hadiah sesuai yang tertulis pada bagian ketentuan
            umum.
          </span>

          <div class="border border-slate-400 my-2"></div>
          <span class="font-bold text-slate-500 sm:text-lg md:text-xl">
            Lain-Lain
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            1) Setiap keputusan dari tim juri bersifat mutlak dan tidak dapat
            diganggu gugat
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            2) Seluruh materi dalam bentuk soal dan pelaksanaan Logicode 2025
            bersifat rahasia dan tidak boleh disebarluaskan selama pelaksanaan
            kompetisi. Soal-soal dalam suatu babak boleh dibagikan apabila
            pelaksanaan babak tersebut telah selesai dilaksanakan
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            3) Peserta yang melanggar ketentuan-ketentuan yang sudah disebutkan
            diatas akan didiskualifikasi dari kompetisi Logicode 2025
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            4) Segala teknis peraturan setiap babak pada website ini baru
            bersifat umum. Peraturan lebih detil akan disampaikan lebih lanjut
            pada saat technical meeting dengan peserta
          </span>
          <span class="text-slate-500 sm:text-lg md:text-xl">
            5) Pertanyaan lebih lanjut mengenai Logicode 2025 dapat diajukan
            melalui tim Kokocoder melalui nomor whatsapp berikut ini :
            <br />
            <ul>
              <li>&nbsp; &nbsp; • +62-877-8585-7166 (Monica)</li>
              <li>&nbsp; &nbsp; • +62-858-1124-5759 (Arnold)</li>
            </ul>
          </span>
        </div>

        <div
          class="text-center text-sm text-slate-600 font-bold cursor-pointer py-1 sticky bottom-0 bg-gradient-to-t from-slate-300 to-transparent w-full"
          @click="expanded = !expanded"
        >
          {{ !expanded ? "Show Full " : "Show Less " }}
          <i
            class="bx"
            :class="[
              {
                'bx-down-arrow-alt': !expanded,
                'bx-up-arrow-alt': expanded,
              },
            ]"
          ></i>
        </div>
      </div>

      <div class="flex flex-col items-center gap-2">
        <!-- <div class="flex gap-4">
          <button
            class="border-2 border-slate-500 py-2 px-14 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
            @click="spawnEmoji('🔥')"
          >
            <span class="text-xl">🔥</span>
          </button>
          <button
            class="border-2 border-slate-500 py-2 px-14 rounded-xl bg-opacity:50 hover:bg-slate-100 cursor-pointer transition-all"
            @click="spawnEmoji('😲')"
          >
            <span class="text-xl">😲</span>
          </button>
        </div> -->
        <button
          class="py-4 px-28 rounded-xl bg-slate-50 bg-opacity:50 cursor-pointer transition-all"
          @click="$emit('scrollToSection', 'testimonials')"
        >
          <span class="flex gap-2 text-lg font-bold">
            NEXT <i id="rules-next" class="bx bx-down-arrow-alt"></i>
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
      expanded: false,
    };
  },
  mounted() {
    this.animateNextArrow();
  },
  methods: {
    animateNextArrow() {
      this.$gsap.to("#rules-next", {
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

      document.getElementById("rules").appendChild(newDiv);

      this.$gsap.timeline().fromTo(
        newDiv,
        { fontSize: "24px", opacity: 1, top: `${y}%` },
        {
          fontSize: "144px",
          opacity: 0,
          display: "none",
          duration: !this.expanded ? 1.5 : 2.5,
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
          ".rules-title",
          { opacity: 0, x: "-40px" },
          { opacity: 1, x: "0px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".rules-description",
          { opacity: 0 },
          { opacity: 1, duration: 1 }
        );
    },
    leaveSection() {
      this.$gsap
        .timeline()
        .fromTo(
          ".rules-title",
          { opacity: 1, x: "0px" },
          { opacity: 0, x: "-40px", duration: 1 }
        );
      this.$gsap
        .timeline()
        .fromTo(
          ".rules-description",
          { opacity: 1 },
          { opacity: 0, duration: 1 }
        );
    },
  },
};
</script>

<style></style>
