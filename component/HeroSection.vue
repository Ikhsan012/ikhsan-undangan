<script setup>
const mempelaiPria = "Pria"
const mempelaiWanita = "Wanita"
</script>

<template>
  <div class="hero-container" id="hero">
    <h4>The Wedding Of</h4>
    <h1>{{ mempelaiWanita }} & {{ mempelaiPria }}</h1>
    <p>Kami ingin mengundang Anda ke dalam perayaan cinta kami.</p>
  </div>
</template>

<style scoped>
.hero-container {
  padding: 80px 20px;
  background-image: url('/src/image/bg.jpeg');
  background-size: cover;
  background-position: center;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

h1 {
  font-size: 3rem;
  margin: 10px 0;
}

h4 {
  font-size: 1.2rem;
}
</style>