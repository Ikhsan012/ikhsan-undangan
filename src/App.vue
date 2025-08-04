<script setup>
import { ref, onMounted } from 'vue';
import HeroSection from '../component/HeroSection.vue';
import DetailAcara from '../component/DetailAcara.vue'
import HitungMundur from '../component/HitungMundur.vue'
import Pesan from '../component/Pesan.vue'
import GaleriPoto from '../component/GaleriPoto.vue';
import Cover from '../component/Cover.vue'
import Navbar from '../component/Navbar.vue';
import AyatSuci from '../component/AyatSuci.vue';
import ProfilMempelai from '../component/ProfilMempelai.vue';
import MiniMap from '../component/MiniMap.vue';
const isInvitationOpen = ref(false);

const guestName = ref('Tamu Undangan');

const audioPlayer = ref(null);

onMounted(() => {
  const urlParams = new URLSearchParams(window.location.search);
  const to = urlParams.get('to');
  if (to) {
    guestName.value = to.replace(/\+/g, ' ');
  }
});

function openInvitation() {
  isInvitationOpen.value = true;
  if (audioPlayer.value) {
    audioPlayer.value.play();
  }
}
</script>

<template>
  <Cover v-if="!isInvitationOpen" :nama-tamu="guestName" @open="openInvitation" />

  <div v-if="isInvitationOpen">
    <Navbar /><main class="container">
      <HeroSection id="hero" /> <ProfilMempelai id="mempelai" />
      <AyatSuci id="ayat" />
      <DetailAcara id="acara" />
      <HitungMundur />
      <GaleriPoto id="galeri" />
      <MiniMap id="lokasi" />
      <Pesan id="rsvp" />
    </main>
  </div>

  <audio ref="audioPlayer" src="/audio/musik.mp3" loop></audio>
</template>

<style scoped>
.container {
  font-family: 'Times New Roman', Times, serif;
  max-width: 500px;
  margin: 0 auto;
  background-color: #fdfaf6;
  color: #5d5d5d;
  text-align: center;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
  animation: fadeIn 1.5s ease-in-out;
}
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
</style>

<style>
:root {
  --font-primary: 'Cormorant Garamond', serif;
  --font-display: 'Dancing Script', cursive;
  --color-gold: #c59d5f;
  --color-dark: #5d5d5d;
  --color-bg-light: #fdfaf6;
  --color-bg-medium: #f7f0e8;
  --color-bg-body: #f0f0f0;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  font-family: var(--font-primary);
  background-color: var(--color-bg-body);
  color: var(--color-dark);
}

h2 {
  font-family: var(--font-display);
  font-size: 3rem;
  color: var(--color-gold);
  margin-top: 0;
  margin-bottom: 30px;
}

.container {
  max-width: 500px;
  margin: 0 auto;
  background-color: var(--color-bg-light);
  box-shadow: 0 0 25px rgba(0, 0, 0, 0.1);
  animation: fadeIn 1.5s ease-in-out;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Perbaikan untuk Form RSVP */
.rsvp-form input[type="text"],
.rsvp-form input[type="number"],
.rsvp-form textarea {
  background-color: #f7f0e8;
  border: 1px solid #e0d9d0;
  transition: border-color 0.3s, box-shadow 0.3s;
}

.rsvp-form input:focus, .rsvp-form textarea:focus {
  outline: none;
  border-color: var(--color-gold);
  box-shadow: 0 0 5px rgba(197, 157, 95, 0.5);
}

.rsvp-form button {
  background-color: var(--color-gold);
}
.rsvp-form button:hover {
  background-color: #b38e54;
}
@media (max-width: 480px) {
  /* Kurangi ukuran font heading agar tidak terlalu besar */
  h2 {
    font-size: 2.6rem;
  }

  /* Kurangi ukuran padding di beberapa section agar konten lebih lega */
  .ayat-container,
  .profil-container,
  .peta-container {
    padding-top: 40px;
    padding-bottom: 40px;
  }

  /* Pastikan hitung mundur tidak terlalu rapat */
  .timer {
    gap: 10px;
    justify-content: center;
    flex-wrap: wrap; /* Izinkan item pindah ke baris baru jika tidak muat */
  }
  
  .time-box {
    width: 65px; /* Sedikit perkecil kotak waktu */
    padding: 8px;
  }

  .time-value {
    font-size: 1.8rem;
  }
}

/* Untuk layar HP yang sangat kecil (lebar di bawah 360px) */
@media (max-width: 360px) {
  h2 {
    font-size: 2.2rem;
  }
  
  .guest-name { /* Ukuran nama tamu di halaman sampul */
    font-size: 2rem;
  }

  /* Ubah galeri menjadi 1 kolom agar foto lebih besar dan jelas */
  .gallery-grid {
    grid-template-columns: 1fr;
  }
}
</style>