<script setup>
import { RouterLink, RouterView } from 'vue-router'
import {ref} from "vue";

const classMenu = ref("-translate-x-full");
const classRota = ref("")
const menuopen = () => {
  if (classMenu.value == "-translate-x-full"){
    classMenu.value = ""
    classRota.value = "rotate-90"
  } else {
    console.log('coucou')
    classMenu.value = "-translate-x-full"
    classRota.value = "rotate-0"
  }
}

</script>

<template>
  <header>

<!--      <nav>-->

<!--      </nav>-->
    <div class="relative min-h-screen md:flex">
      <!-- mobile navbar -->
      <div class="bg-gray-800 text-gray-100 flex justify-between md:hidden">
        <!-- logo -->
        <RouterLink class="block p-4 text-white font-bold" to="/">PTM</RouterLink>
        <!-- mobile menu -->
        <button v-on:click="menuopen" :class="classRota" class=" p-4 focus:outline-none focus:bg-gray-700">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 10h16M4 14h16M4 18h16"></path></svg>
        </button>
      </div>


      <!-- sidebar -->
      <div :class="classMenu" class="bg-blue-800 text-blue-100 w-64 space-y-6 py-7 px-2 absolute inset-y-0 left-0 transform md:relative md:translate-x-0 transition duration-200 ease-in-out">
        <!-- logo -->
        <a href="#" class="flex items-center text-white space-x-2 px-4">
          <RouterLink class="block p-4 text-white font-bold text-2xl font-extrabold" to="/">PTM</RouterLink>
        </a>
        <!-- nav -->
        <nav>
          <a href="#" class="block py-2.5 px-4 rounded transition duration-200 hover:bg-blue-700 hover:text-white">Home</a>
          <a href="#" class="block py-2.5 px-4 rounded hover:bg-blue-700">About</a>
          <a href="#" class="block py-2.5 px-4 rounded hover:bg-blue-700">Features</a>
          <a href="#" class="block py-2.5 px-4 rounded hover:bg-blue-700">Pricing</a>
        </nav>

      </div>

      <!-- main content -->
      <div class="flex-1 p-10 text-2xl font-bold">
        <RouterView />
      </div>
    </div>
  </header>


</template>

<style scoped>

</style>
