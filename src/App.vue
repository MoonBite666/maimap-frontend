<script setup>
import Logo from '@/components/Logo.vue'
import SearchBar from '@/components/SearchBar.vue'
</script>

<template>
  <div id="app">
    <div class="center-container">
      <Logo />
      <SearchBar />

    </div>
  </div>
</template>



<style scoped>
#app {
  color: #2c3e50;
}

.center-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 50vh;
  text-align: center;
  width: 100%;
}


</style>