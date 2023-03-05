<script lang="ts">
import useStore from '../services/store';
// import sound_black from '../assets/image/sound.png';

export default {
  setup() {
    const store = useStore();
    return { store };
  },
  data() {
    return {
      colorModal: false,
      color: {
        white: 'white',
        black: 'black',
        red: 'red',
        green: 'green',
        blue: 'blue',
        purple: 'purple',
        pink: 'pink',
        violet: 'violet',
        sound_white: '../assets/img/sound-white.png',
        mute_black: '../assets/img/mute.png',
        mute_white: '../assets/img/mute-white.png',
        // sound_black
      }
    }
  }
}
</script>
<template>
<div>
<div class="z-50 absolute top-0 -bottom-50 h-full left-0 right-0 w-full" @click="colorModal=false" v-if="colorModal"></div>
<div class="flex justify-center p-4">
  <!-- Dark/Light button -->
  <button class="rounded-full h-8 w-8 m-2 flex justify-center items-center shadow-xl" 
  @click="[store.switchDark(),
  store.color.includes('white') && !store.dark ? store.changeColor(store.color.replace('white', 'black')) : '',
  store.color.includes('black') && store.dark ? store.changeColor(store.color.replace('black', 'white')) : '']" 
  :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
    <svg v-if="store.dark" xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z" />
    </svg>
    <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" />
    </svg>
  </button>
  <!-- Sound button -->
  <button class="rounded-full h-8 w-8 m-2 flex justify-center items-center shadow-xl" 
  @click="store.switchSound()" 
  :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
    <img alt="Sound" v-if="store.sound" :src="store.dark ? 'sound_white' : 'sound_black'" class="h-4 w-4"/>
    <img alt="Sound" v-else :src="store.dark ? 'mute_white' : 'mute_black'" class="h-4 w-4"/>
  </button>
  <!-- Color buttons -->
  <button 
  class="rounded-full h-8 w-8 m-2 flex justify-center items-center shadow-xl"
  @click="colorModal=!colorModal"
  :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
    <div class="h-4 w-4 rounded-full"
    :class="`bg-${store.color}`"></div>
    <div v-if="colorModal"
    class="z-50 absolute mt-72 py-4 flex flex-wrap justify-center w-36 p-2 rounded-xl shadow-xl"
    :class="store.dark ? 'bg-black/90 shadow-gray-700' : 'bg-white'">
      <!-- Dark mode -->
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('white/90'), store.changeHeart('🤍')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'"
      v-if="store.dark">
        <div class="h-4 w-4 bg-white/90 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('white/60'), store.changeHeart('🤍')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'"
      v-if="store.dark">
        <div class="h-4 w-4 bg-white/60 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('white/20'), store.changeHeart('🤍')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'"
      v-if="store.dark">
        <div class="h-4 w-4 bg-white/20 rounded-full"></div>
      </button>
      <!-- Light mode -->
      <div class="flex" v-if="!store.dark">
        <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
        @click="[store.changeColor('black/90'), store.changeHeart('🖤')]"
        :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
          <div class="h-4 w-4 bg-black/90 rounded-full"></div>
        </button>
        <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
        @click="[store.changeColor('black/60'), store.changeHeart('🖤')]"
        :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
          <div class="h-4 w-4 bg-black/60 rounded-full"></div>
        </button>
        <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl"
        @click="[store.changeColor('black/20'), store.changeHeart('🖤')]"
        :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
          <div class="h-4 w-4 bg-black/20 rounded-full"></div>
        </button>
      </div>
      <!-- Red colors -->
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl"
      @click="[store.changeColor('red-500'), store.changeHeart('❤️')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-red-500 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl"
      @click="[store.changeColor('orange-500'), store.changeHeart('🧡')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-orange-500 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('yellow-500'), store.changeHeart('💛')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-yellow-500 rounded-full"></div>
      </button>
      <!-- Green colors -->
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('green-500'), store.changeHeart('💚')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-green-500 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('lime-500'), store.changeHeart('💚')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-lime-500 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl"
      @click="[store.changeColor('emerald-500'), store.changeHeart('💚')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-emerald-300 rounded-full"></div>
      </button>
      <!-- Blue colors -->
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl"
      @click="[store.changeColor('blue-500'), store.changeHeart('💙')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-blue-600 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('sky-500'), store.changeHeart('💙')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-sky-500 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('cyan-500'), store.changeHeart('💙')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-cyan-400 rounded-full"></div>
      </button>
      <!-- Pink colors -->
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('purple-500'), store.changeHeart('💜')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-purple-500 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl" 
      @click="[store.changeColor('fuchsia-500'), store.changeHeart('💜')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-fuchsia-500 rounded-full"></div>
      </button>
      <button class="rounded-full h-8 w-8 m-1 flex justify-center items-center shadow-xl"
      @click="[store.changeColor('pink-500'), store.changeHeart('💗')]"
      :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">
        <div class="h-4 w-4 bg-pink-500 rounded-full"></div>
      </button>
    </div>
  </button>
  <!-- Github Button -->
    <button class="rounded-full h-8 w-8 m-2 flex justify-center items-center shadow-xl" 
    @click="[store.switchDark(),
    store.color.includes('white') && !store.dark ? store.changeColor(store.color.replace('white', 'black')) : '',
    store.color.includes('black') && store.dark ? store.changeColor(store.color.replace('black', 'white')) : '']" 
    :class="store.dark ? 'bg-white/10 shadow-gray-700 border-white/20 hover:bg-gray-600 text-white' : 'bg-white hover:bg-gray-200 border-black/20 text-gray-600'">

    </button>
</div>
<div class="bg-black/90 text-black/90 shadow-black/90 border-black/90"></div>
<div class="bg-black/60 text-black/60 shadow-black/60 border-black/60"></div>
<div class="bg-black/20 text-black/20 shadow-black/20 border-black/20"></div>
<div class="bg-white/90 text-white/90 shadow-white/90 border-white/90"></div>
<div class="bg-white/60 text-white/60 shadow-white/60 border-white/60"></div>
<div class="bg-white/20 text-white/20 shadow-white/20 border-white/20"></div>
<div class="bg-red-500  text-red-500 shadow-red-500 border-red-500"></div>
<div class="bg-orange-500 text-orange-500 shadow-orange-500 border-orange-500"></div>
<div class="bg-yellow-500 text-yellow-500 shadow-yellow-500 border-yellow-500"></div>
<div class="bg-green-500 text-green-500 shadow-green-500 border-green-500"></div>
<div class="bg-emerald-500 text-emerald-500 shadow-emerald-500 border-emerald-500"></div>
<div class="bg-lime-500 text-lime-500 shadow-lime-500 border-lime-500 "></div>
<div class="bg-blue-500 text-blue-500 shadow-blue-500 border-blue-500 "></div>
<div class="bg-sky-500  text-sky-500  shadow-sky-500 border-sky-500 "></div>
<div class="bg-cyan-500 text-cyan-500 shadow-cyan-500 border-cyan-500 "></div>
<div class="bg-purple-500 text-purple-500 shadow-purple-500 border-purple-500"></div>
<div class="bg-fuchsia-500 text-fuchsia-500 shadow-fuchsia-500 border-fuchsia-500"></div>
<div class="bg-pink-500 text-pink-500 shadow-pink-500 border-pink-500"></div>
</div>
</template>