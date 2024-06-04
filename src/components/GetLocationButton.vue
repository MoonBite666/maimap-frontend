<script setup>

</script>

<template>
  <button @click="getLocation">获取位置</button>
</template>

<script>
export default {
  methods: {
    getLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
            (position) => {
              this.$emit('location-received', `Latitude: ${position.coords.latitude}, Longitude: ${position.coords.longitude}`);
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

</style>