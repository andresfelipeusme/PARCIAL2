<template>
  <div>
    <header class="header">
      <div class="logo">facebook</div>
      <input type="text" class="search-bar" placeholder="Buscar..." />
      <nav class="nav">
        <button @click="current = 'muro'">Muro</button>
        <button @click="current = 'info'">Info</button>
        <button @click="current = 'photos'">Fotos</button>
        <button @click="current = 'boxes'">Cajas</button>
      </nav>
    </header>

    <div class="container">
      <aside class="sidebar-left">
        <img src="/assets/perfil.png" alt="Perfil" class="perfil-img" />
        <h2 class="nombre">Andres Usme</h2>
        <p class="info">Información</p>
        <p>info</p>
        <p>X Amigos</p>
        <div class="amigos">
          <div class="amigo"></div>
          <div class="amigo"></div>
          <div class="amigo"></div>
        </div>
        <a href="#">ver todo</a>
      </aside>

      <main class="main-content">
        <component :is="currentComponent" />
      </main>

      <aside class="sidebar-right">
        <div class="box">
          <p>Compartir algo</p>
          <button class="btn">Compartir</button>
        </div>
      </aside>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import Muro from './components/Muro.vue'
import Info from './components/Info.vue'
import Photos from './components/Photos.vue'
import Boxes from './components/Boxes.vue'

const current = ref('muro')
const currentComponent = computed(() => {
  return { muro: Muro, info: Info, photos: Photos, boxes: Boxes }[current.value]
})
</script>

<style>
@import './styles.css';
</style>