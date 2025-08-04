<script setup>
const ayat = "Dan di antara tanda-tanda (kebesaran)-Nya ialah Dia menciptakan pasangan-pasangan untukmu dari jenismu sendiri, agar kamu cenderung dan merasa tenteram kepadanya, dan Dia menjadikan di antaramu rasa kasih dan sayang. Sungguh, pada yang demikian itu benar-benar terdapat tanda-tanda (kebesaran Allah) bagi kaum yang berpikir.";
const sumber = "QS. Ar-Rum: 21";
</script>

<template>
  <div class="ayat-container" id="ayat">
    <div class="content">
      <p class="ayat-text">"{{ ayat }}"</p>
      <p class="sumber-text">{{ sumber }}</p>
    </div>
  </div>
</template>

<style scoped>
.ayat-container {
  padding: 60px 20px;
  background-color: #f7f0e8; /* Warna latar yang lembut */
  text-align: center;
  position: relative;
  overflow: hidden; /* Agar dekorasi tidak keluar */
}

/* Elemen dekoratif bunga (opsional) */
.ayat-container::before {
  content: '';
  position: absolute;
  top: -20px;
  left: -30px;
  width: 150px;
  height: 150px;
  background: url('/images/flower-corner.svg') no-repeat; /* Anda perlu menyediakan gambar ini */
  background-size: contain;
  opacity: 0.2;
  transform: rotate(0deg);
}
.ayat-container::after {
  content: '';
  position: absolute;
  bottom: -20px;
  right: -30px;
  width: 150px;
  height: 150px;
  background: url('/images/flower-corner.svg') no-repeat;
  background-size: contain;
  opacity: 0.2;
  transform: rotate(180deg);
}

.ayat-text {
  font-size: 1.1rem;
  font-style: italic;
  line-height: 1.8;
  margin-bottom: 20px;
}

.sumber-text {
  font-weight: bold;
  font-size: 1.2rem;
  color: #c59d5f; /* Warna emas */
}
</style>