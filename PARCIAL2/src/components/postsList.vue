<!-- src/components/Muro.vue -->
<template>
  <div>
    <!-- Campo de texto y botón compartir -->
    <textarea
      v-model="newText"
      placeholder="Pon algo aquí..."
      rows="3"
    ></textarea>
    <button class="btn" @click="addPost">Compartir</button>
    <hr />

    <!-- Lista de publicaciones -->
    <div class="post" v-for="p in posts" :key="p.id">
      <p><strong>{{ p.user }}</strong> - {{ p.time }}</p>
      <p>{{ p.text }}</p>
      <a v-if="p.comments > 0" href="#">
        Ver los {{ p.comments }} comentarios
      </a>
      <div v-for="(img, j) in p.images" :key="j">
        <img :src="img" alt="imagen de publicación" />
      </div>

      <!-- Acciones -->
      <div class="actions">
        <button class="btn-small" @click="onLike(p.id)">👍 Me gusta</button>
        <button class="btn-small" @click="onShare(p.id)">↗ Compartir</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const posts = ref([
  {
    id: 1,
    user: 'Camila',
    time: 'Última Publicación Lunes a las 8:45pm',
    text: 'Me gusta 👍',
    comments: 6,
    images: ['/assets/mujer.jpg', '/assets/perfil.png']
  },
  {
    id: 2,
    user: 'Andrea',
    time: 'Publicó a las 11:46pm',
    text: 'Otra publicación...',
    comments: 0,
    images: ['/assets/perfil.png']
  },
  {
    id: 3,
    user: 'Karina',
    time: 'Martes a las 9:00am',
    text: '¡Hoy es un gran día! 🌞',
    comments: 3,
    images: ['/assets/perfil.png', '/assets/mujer.jpg']
  },
  {
    id: 4,
    user: 'Carolina',
    time: 'Martes a las 12:30pm',
    text: 'Visitando un nuevo lugar...',
    comments: 4,
    images: ['/assets/mujer.jpg', '/assets/perfil.png']
  },
  {
    id: 5,
    user: 'Esmeralda',
    time: 'Miércoles a las 1:45pm',
    text: '¡Qué divertido es aprender a programar! 💻',
    comments: 2,
    images: ['/assets/mujer.jpg', '/assets/mujer.jpg']
  }
])

const newText = ref('')

function addPost() {
  const text = newText.value.trim()
  if (!text) return
  posts.value.unshift({
    id: Date.now(),
    user: 'Andres Usme',
    time: 'Ahora',
    text,
    comments: 0,
    images: []
  })
  newText.value = ''
}

function onLike(id) {
  console.log('liked', id)
}

function onShare(id) {
  console.log('shared', id)
}
</script>

<style scoped>
textarea {
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 8px;
  margin-bottom: 10px;
}
.btn {
  background: #3b5998;
  color: white;
  border: none;
  padding: 10px 14px;
  border-radius: 4px;
  margin-top: 8px;
  cursor: pointer;
}
.btn:hover {
  background: #2d4373;
}

.post {
  background: #f7f7f7;
  padding: 10px;
  border-radius: 3px;
  margin-top: 10px;
}
.post img {
  width: 100%;
  max-width: 400px;
  margin-top: 10px;
  border-radius: 4px;
}
.actions {
  display: flex;
  gap: 10px;
  margin-top: 8px;
}
.btn-small {
  background: #dfe3ee;
  color: #3b5998;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 8px;
  cursor: pointer;
}
.btn-small:hover {
  background: #f7f7f7;
}
</style>
