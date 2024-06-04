<template>
  <div id="app">
    <div class="center-container">
      <div class="logo">
        <h1>MaiMap</h1>
      </div>
      <div class="search">
        <input type="text" v-model="searchQuery" placeholder="Search..." />
        <button @click="search">查询</button>
        <button @click="getLocation">获取位置</button>
      </div>
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

.logo {
  margin-bottom: 40px;
}

.search input {
  margin-right: 10px;
}
</style>