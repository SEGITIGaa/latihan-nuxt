<script setup>
import Navbar from '../components/navbar.vue';
</script>
<template>
  <div class="flex flex-col gap-10 px-5 md:px-0 md:w-5/6 mx-auto">
    <header>
      <Navbar />
    </header>
    <main>
      <!-- MAIN CONTENT -->
      <slot/>
    </main>
    <footer>
      <p>ini adalah footer</p>
    </footer>
  </div>
</template>