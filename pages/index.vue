<template>
  <div class="video-bg">
    <!-- YouTube iframe -->
    <iframe
      :src="youtubeUrl"
      frameborder="0"
      allow="autoplay; fullscreen"
      allowfullscreen
      @load="onVideoLoad"
      :class="{ visible: videoLoaded }"
    ></iframe>

    <!-- Затемнение поверх видео -->
    <!-- <div class="overlay"></div> -->

    <!-- Контент -->
    <div class="content" :class="{ visible: videoLoaded }">
            <h1 class="welcome-text">Добро пожаловать</h1>
      <p> на сайт по сериалу "Очень странные дела"</p>
    </div>
  </div>
 
</template>

<script setup>
import { ref } from 'vue'

const youtubeId = 'phrT6RoM038' // замените на ID вашего видео (например 'dQw4w9WgXcQ')
const youtubeUrl = `https://www.youtube.com/embed/${youtubeId}?autoplay=1&mute=1&loop=1&playlist=${youtubeId}&controls=0&showinfo=0&modestbranding=1`

const videoLoaded = ref(false)
const onVideoLoad = () => {
  // плавное появление видео после загрузки iframe
  setTimeout(() => (videoLoaded.value = true), 300)
}
</script>

<style scoped>
.video-bg {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  z-index: -10;
}

/* Делаем iframe как "background-cover" */
iframe {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 177.78vh; /* пропорция 16:9 → 100 * 16 / 9 = 177.78 */
  height: 100vh;
  transform: translate(-50%, -50%);
  opacity: 0;
  transition: opacity 1.5s ease;
  pointer-events: none;
  z-index: -2;
}

@media (min-aspect-ratio: 16/9) {
  iframe {
    width: 100vw;
    height: 56.25vw; /* 100 * 9 / 16 = 56.25 */
  }
}

iframe.visible {
  opacity: 1;
}

/* Затемнение */
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.4);
  z-index: -1;
}

/* Контент */
.content {
  position: relative;
  color: white;
  text-align: center;
  top: 20%;
  transform: translateY(-40%);
  opacity: 0;
  p: bold; 
  transition: opacity 1.2s ease 0.5s;
}

 .welcome-text {
  font-size: 3rem;       /* большой размер */
  font-weight: 800;      /* очень жирный */

}

.content.visible {
  opacity: 1;
}
</style>