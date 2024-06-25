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
                    localStorage.setItem('location', data.result.formatted_addresses.recommend);
                    localStorage.setItem('lat', data.result.ad_info.location.lat);
                    localStorage.setItem('lng', data.result.ad_info.location.lng);
                    localStorage.setItem('province', data.result.address_component.province);
                    localStorage.setItem('city', data.result.address_component.city);
                    this.$emit('location-received', data.result.formatted_addresses.recommend);
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