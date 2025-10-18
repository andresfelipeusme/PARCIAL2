<!-- src/components/Post.vue -->
<template>
  <article class="post">
    <p><strong>{{ post.user }}</strong> - {{ post.time }}</p>
    <p>{{ post.text }}</p>

    <a v-if="post.comments" href="#">Ver los {{ post.comments }} comentarios</a>

    <div v-for="(img, i) in post.images" :key="i" style="margin-top:10px">
      <img :src="img" alt="imagen" />
    </div>

    <div class="post-actions">
      <button @click="$emit('like', post.id)">Me gusta</button>
      <button @click="$emit('share', post.id)">Compartir</button>
    </div>
  </article>
</template>

<script setup>
defineProps({
  post: {
    type: Object,
    required: true
  }
})
</script>

<style>
.post {
  background: #f7f7f7;
  padding: 12px;
  border-radius: 4px;
  margin-top: 15px;
}
.post img {
  width: 100%;
  max-width: 400px;
  display: block;
  margin: 10px auto;
  border-radius: 4px;
}
.post-actions { margin-top: 8px; display:flex; gap:8px; }
</style>