<script setup>
import SearchButton from "@/components/SearchButton.vue";
import GetLocationButton from "@/components/GetLocationButton.vue";
</script>

<template>
  <div class="search">
    <input type="text" v-model="searchQuery" placeholder="输入任意位置开始……" />
    <SearchButton :query="searchQuery"/>
    <GetLocationButton @location-received="handleLocationReceived" />

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

    handleLocationReceived(location) {
      this.searchQuery = location;
    },
  },
};
</script>
<style scoped>
.search input {
  margin-right: 10px;
}
</style>