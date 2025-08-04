<script setup>
const acara = [{
    nama: "Akad Nikah",
    waktu: "09:00 - 10:00 WIB",
    tanggal: "Sabtu, 12 September 2025",
    tempat: "Masjid Jakarta"
}, {
    nama: "Resepsi",
    waktu: "09:00 - 10:00 WIB",
    tanggal: "Sabtu, 12 September 2025",
    tempat: "Masjid Jakarta"
}]
</script>

<template>
  <div class="acara-container" id="acara">
    <h2>Detail Acara</h2>
    <div v-for="item in acara" :key="item.nama" class="acara-card">
      <h3>{{ item.nama }}</h3>
      <p>{{ item.waktu }}</p>
      <p>{{ item.tanggal }}</p>
      <p>{{ item.tempat }}</p>
    </div>
  </div>
</template>

<style scoped>
.acara-container {
  padding: 40px 20px;
}

.acara-card {
  background-color: #ffffff;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.05);
}

h2 {
  margin-bottom: 30px;
}
</style>