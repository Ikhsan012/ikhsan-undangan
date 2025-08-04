<script setup>

const daftarFoto = [
  '/images/foto1.jpg',
  '/images/foto2.jpg',
  '/images/foto3.jpg',
  '/images/foto4.jpg',
  '/images/foto5.jpg',
  '/images/foto6.jpg',
];
</script>

<template>
  <div class="gallery-container" id="galeri">
    <h2>Momen Bahagia Kami</h2>
    <div class="gallery-grid">
      <div v-for="(foto, index) in daftarFoto" :key="index" class="gallery-item">
        <img :src="foto" alt="Foto Galeri" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.gallery-container {
  padding: 40px 20px;
  background-color: #fdfaf6;
}

h2 {
  text-align: center;
  margin-bottom: 30px;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr); 
  gap: 15px; 
}

.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover; 
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease; 
}

.gallery-item img:hover {
  transform: scale(1.05); 
}
</style>