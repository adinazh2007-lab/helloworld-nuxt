<template>
<main class="flex flex-col gap-4 p-12 justify-center min-h-screen items-center bg-gradient-to-b from-black to-red-900 flex-wrap">
  <div class="flex gap-4">
    <label><input class="mx-2" type="radio" value="argyle" v-model="selectedpic">Argyle</label>
    <label><input class="mx-2" type="radio" value="billy" v-model="selectedpic">Billy</label>
    <label><input class="mx-2" type="radio" value="dustin" v-model="selectedpic">Dustin</label>
  </div>
  <div class="flex flex-row gap-4 flex-wrap justify-center">
    <div class="blockcap" v-if="selectedpic == 'argyle'"> 
      <img :src="pic1.image" class="w-60 h-60 pt-2">
      <p class="text-black text-xl">{{pic1.name}}</p>
    </div>
    <div class="blockcap" v-if="selectedpic == 'billy'"> 
      <img :src="pic2.image" class="w-60 h-60 pt-2">
      <p class="text-black text-xl">{{pic2.name}}</p>
    </div>
        <div class="blockcap" v-if="selectedpic == 'dustin'"> 
      <img :src="pic3.image" class="w-60 h-60 pt-2">
      <p class="text-black text-xl">{{pic3.name}}</p>
    </div>
  </div>

  <div class="flex flex-row gap-4 flex-wrap justify-center">
    <div class="blockfor" v-for="(pic, index) in genpic" :key = "index">
      <img :src="pic.image" class="w-60 h-60 pt-2">
      <p class="text-black text-xl">{{ pic.name }}</p>
    </div>
  </div>
</main>
</template>

<script setup lang="ts">

import {reactive,ref} from 'vue'

interface stking{
  name:string,
  image:string
}

const pic1 = reactive<stking>({
  name:'argyle',
  image:"/img/argyle.webp"
})

const pic2 = reactive<stking>({
  name:'billy',
  image:"/img/billy.webp"
})

const pic3 = reactive<stking>({
  name:'dustin',
  image:"/img/dustin.webp"
})

// const pic4 = reactive<stking>({
//   name:'eddie',
//   image:"/img/eddie.webp"
// })

// const pic5 = reactive<stking>({
//   name:'eleven',
//   image:"/img/eleven.webp"
// })

// const pic6 = reactive<stking>({
//   name:'jim',
//   image:"/img/jim.webp"
// })

// const pic7 = reactive<stking>({
//   name:'jonathan',
//   image:"/img/jonathan.webp"
// })

// const pic8 = reactive<stking>({
//   name:'lucas',
//   image:"/img/lucas.webp"
// })

// const pic9 = reactive<stking>({
//   name:'max',
//   image:"/img/max.webp"
// })

// const pic10 = reactive<stking>({
//   name:'mike',
//   image:"/img/mike.webp"
// })

// const pic11 = reactive<stking>({
//   name:'nancy',
//   image:"/img/nancy.webp"
// })

// const pic12 = reactive<stking>({
//   name:'robin',
//   image:"/img/robin.webp"
// })

// const pic13 = reactive<stking>({
//   name:'steve',
//   image:"/img/steve.webp"
// })

// const pic14 = reactive<stking>({
//   name:'vecna',
//   image:"/img/vecna.webp"
// })

// const pic15 = reactive<stking>({
//   name:'will',
//   image:"/img/will.webp"
// })


const genpic = reactive<stking[]>([
  // {name:'argyle', image:"/img/argyle.webp"},
  // {name:'billy', image:"/img/billy.webp"},
  // {name:'dustin', image:"/img/dustin.webp"},
  {name:'eddie', image:"/img/eddie.webp"},
  {name:'eleven', image:"/img/eleven.webp"},
  {name:'jim', image:"/img/jim.webp"},
  {name:'jonathan', image:"/img/jonathan.webp"},
  {name:'lucas', image:"/img/lucas.webp"},
  {name:'max', image:"/img/max.webp"},
  {name:'mike', image:"/img/mike.webp"},
  {name:'nancy', image:"/img/nancy.webp"},
  {name:'robin', image:"/img/robin.webp"},
  {name:'steve', image:"/img/steve.webp"},
  {name:'vecna', image:"/img/vecna.webp"},
  {name:'will', image:"/img/will.webp"}
])

const selectedpic=ref<stking>('')

</script>

<style scoped>

.blockcap {
  @apply flex flex-col gap-2 border-white border w-72 h-auto items-center hover:border-red-900 hover:bg-red-900 rounded-xl;
}

.blockfor{
  @apply flex flex-col gap-2 border-white border w-72 h-auto items-center hover:border-red-900 hover:bg-red-900 rounded-xl;
}
</style>