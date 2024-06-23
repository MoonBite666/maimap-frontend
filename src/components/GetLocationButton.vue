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
              fetch(`http://localhost:8080/rgc?lat=${position.coords.latitude}&lng=${position.coords.longitude}`)
                  .then(response => {
                    console.log(response);
                    return response.json();
                  })
                  .then(data => {
                    console.log(data);
                    this.$emit('location-received', data.result.formatted_address);
                  })
                  .catch(error => {
                    console.error('Error occurred while getting location: ', error);
                  });
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