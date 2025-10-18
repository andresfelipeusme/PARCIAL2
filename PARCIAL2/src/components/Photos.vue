<template>
  <div>
    <h2>Fotos</h2>
    <div class="photos-grid">
      <div class="amigo" v-for="(img, i) in fotos" :key="i">
        <img :src="img" alt="Foto" />
      </div>
    </div>
  </div>
</template>

<script setup>
const fotos = [
  '/assets/perfil.png',
  '/assets/descarga.jpg',
  '/assets/mujer.jpg',
  '/assets/mujer.jpg',
  '/assets/perfil.png'
]
</script>
