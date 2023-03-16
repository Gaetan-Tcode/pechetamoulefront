<script setup>
import { RouterLink, RouterView } from 'vue-router'
import {ref} from "vue";

// const btn = document.querySelector('.mobile-menu-btn');

const sidebar = document.querySelector('.sidebar');
const classMenu = ref();
const menuopen = () => {
  classMenu.value = '-translate-x-full'
}
</script>

<template>
  <header>

<!--      <h1 class="text-3xl font-bold underline">-->
<!--        Hello world!-->
<!--      </h1>-->

<!--      <nav>-->
<!--        <RouterLink to="/">Accueil</RouterLink>-->
<!--      </nav>-->
    <div class="relative min-h-screen md:flex">
      <!-- mobile navbar -->
      <div class="bg-gray-800 text-gray-100 flex justify-between md:hidden">
        <!-- logo -->
        <a href="#" class="block p-4 text-white font-bold">Better Dev</a>
        <!-- mobile menu -->
        <button v-on:click="menuopen" :class="classMenu" class="mobile-menu-btn p-4 focus:outline-none focus:bg-gray-700">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 10h16M4 14h16M4 18h16"></path></svg>
        </button>
      </div>


      <!-- sidebar -->
      <div class="sidebar bg-blue-800 text-blue-100 w-64 space-y-6 py-7 px-2 absolute inset-y-0 left-0 transform -translate-x-full md:relative md:translate-x-0 transition duration-200 ease-in-out">
        <!-- logo -->
        <a href="#" class="flex items-center text-white space-x-2 px-4">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"></path></svg>
          <span class="text-2xl font-extrabold">Better Dev</span>
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
        main content goes here
      </div>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

</style>
