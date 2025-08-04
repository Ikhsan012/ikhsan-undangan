<template>
  <nav class="navbar">
    <a href="#mempelai"><span>Mempelai</span></a>
    <a href="#acara"><span>Acara</span></a>
    <a href="#galeri"><span>Galeri</span></a>
    <a href="#lokasi"><span>Lokasi</span></a>
    <a href="#rsvp"><span>Links</span></a>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: rgba(253, 250, 246, 0.9); /* Sedikit transparan */
  backdrop-filter: blur(5px);
  display: flex;
  justify-content: space-around;
  padding: 10px 0;
  box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
  z-index: 50;
  max-width: 500px; /* Samakan dengan max-width container */
  left: 50%;
  transform: translateX(-50%);
}

.navbar a {
  text-decoration: none;
  color: #5d5d5d;
  font-size: 0.8rem;
  text-align: center;
}

.navbar a:hover {
  color: #c59d5f;
}
</style>