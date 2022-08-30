<template>
  <div class="p-2 md:p-4">
    <div class='p-2 bg-zinc-50 flex gap-4 border-b-2 border-gray-200'> <!-- menu -->
      <button class="p-2 hover:bg-gradient-to-r hover:from-gray-100 hover:to-gray-200 hover:rounded-xl transition-all duration-500">logo</button>      
      <button class="p-2 hover:bg-gradient-to-r hover:from-gray-100 hover:to-gray-200 hover:rounded-xl transition-all duration-500">Products</button>
      <button class="p-2 hover:bg-gradient-to-r hover:from-gray-100 hover:to-gray-200 hover:rounded-xl transition-all duration-500">Contact us</button>      
    </div>  <!-- menu -->
  <Home/>
  </div>
</template>

<script setup>
import Home from './Home.vue'
</script>

<style scoped>


@font-face {
  font-family: cd;
  src: url(/assets/cd.ttf);
}

</style>
