<template>
  <div class="peta-container" id="lokasi">
    <h2>Lokasi Acara</h2>
    <p class="alamat">
      Gedung Balai Kartini<br>
      Jl. Jend. Gatot Subroto Kav. 37, Jakarta Selatan
    </p>
    <div class="map-wrapper">
      <iframe 
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3966.278918237007!2d106.82030097500001!3d-6.226917893761705!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e69f3e856e7f835%3A0x1927f589831487a!2sBalai%20Kartini!5e0!3m2!1sen!2sid!4v1722760867710!5m2!1sen!2sid" 
        width="600" 
        height="450" 
        style="border:0;" 
        allow="fullscreen" loading="lazy" 
        referrerpolicy="no-referrer-when-downgrade">
      </iframe>
    </div>
    <a href="https://maps.app.goo.gl/yQ3q5C8wF4Z2Z4bJ6" target="_blank" class="map-button">
      Buka di Google Maps
    </a>
  </div>
</template>

<style scoped>
.peta-container {
  padding: 60px 20px;
  background-color: #fdfaf6;
}

.alamat {
  margin-bottom: 20px;
}

.map-wrapper {
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  border: 4px solid #fff;
}

.map-wrapper iframe {
  width: 100%;
  height: 350px;
  display: block;
}

.map-button {
  display: inline-block;
  margin-top: 20px;
  padding: 10px 25px;
  background-color: #c59d5f;
  color: white;
  text-decoration: none;
  border-radius: 20px;
  font-weight: bold;
  transition: background-color 0.3s;
}
.map-button:hover {
  background-color: #b38e54;
}
</style>