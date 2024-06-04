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

<script>
export default {
  data() {
    return {
      searchQuery: '',
    };
  },
  methods: {
    search() {
      console.log('Searching for: ' + this.searchQuery);
    },
    getLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
            (position) => {
              this.searchQuery = `Latitude: ${position.coords.latitude}, Longitude: ${position.coords.longitude}`;
            },
            (error) => {
              console.error('Error occurred while getting location: ', error);
            }
        );
      } else {
        console.error('Geolocation is not supported by this browser.');
      }
    },
  },
};
</script>

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