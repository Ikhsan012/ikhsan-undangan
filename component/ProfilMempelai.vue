<script setup>
const mempelaiPria = {
  namaPanggilan: "Budi",
  namaLengkap: "Budi Hartono",
  namaAyah: "Bpk. H. Abdullah",
  namaIbu: "Ibu Hj. Fatimah",
  fotoUrl: "/src/image/bg.jpeg"
};

const mempelaiWanita = {
  namaPanggilan: "Siti",
  namaLengkap: "Siti Rahmawati",
  namaAyah: "Bpk. H. Ahmad",
  namaIbu: "Ibu Hj. Khadijah",
  fotoUrl: "/src/image/bg.jpeg"
};
</script>

<template>
  <div class="profil-container" id="mempelai">
    <h2>Mempelai</h2>
    <div class="mempelai-wrapper">
      <div class="mempelai-card">
        <img :src="mempelaiWanita.fotoUrl" :alt="mempelaiWanita.namaPanggilan" class="foto-mempelai">
        <h3 class="nama-panggilan">{{ mempelaiWanita.namaPanggilan }}</h3>
        <p class="nama-lengkap">{{ mempelaiWanita.namaLengkap }}</p>
        <p class="nama-orangtua">
          Putri dari Pasangan<br>
          <strong>{{ mempelaiWanita.namaAyah }}</strong> &amp; <strong>{{ mempelaiWanita.namaIbu }}</strong>
        </p>
      </div>

      <div class="ampersand">&amp;</div>
      
      <div class="mempelai-card">
        <img :src="mempelaiPria.fotoUrl" :alt="mempelaiPria.namaPanggilan" class="foto-mempelai">
        <h3 class="nama-panggilan">{{ mempelaiPria.namaPanggilan }}</h3>
        <p class="nama-lengkap">{{ mempelaiPria.namaLengkap }}</p>
        <p class="nama-orangtua">
          Putra dari Pasangan<br>
          <strong>{{ mempelaiPria.namaAyah }}</strong> &amp; <strong>{{ mempelaiPria.namaIbu }}</strong>
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.profil-container {
  padding: 60px 20px;
  background-color: #fdfaf6;
}

.mempelai-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.mempelai-card {
  text-align: center;
}

.foto-mempelai {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid #c59d5f;
  margin-bottom: 15px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
}

.nama-panggilan {
  font-family: 'Dancing Script', cursive;
  font-size: 2.5rem;
  color: #c59d5f;
  margin: 0;
}

.nama-lengkap {
  font-size: 1.2rem;
  font-weight: bold;
  margin-top: 5px;
}

.nama-orangtua {
  font-size: 0.9rem;
  line-height: 1.5;
  margin-top: 10px;
}

.ampersand {
  font-family: 'Dancing Script', cursive;
  font-size: 4rem;
  color: #c59d5f;
  margin: 10px 0;
}
</style>