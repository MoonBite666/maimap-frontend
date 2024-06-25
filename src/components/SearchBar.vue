<script setup>
import SearchButton from "@/components/SearchButton.vue";
import GetLocationButton from "@/components/GetLocationButton.vue";
</script>

<template>
  <div class="search">
    <input type="text" v-model="searchQuery" placeholder="输入任意位置开始……" />
    <ul v-if="suggestions.length">
      <li v-for="(suggestion, index) in suggestions" :key="index">
        {{ suggestion }}
      </li>
    </ul>
    <SearchButton :query="searchQuery"/>
    <GetLocationButton @location-received="handleLocationReceived" />

  </div>
</template>

<script>

export default {
  data() {
    return {
      searchQuery: '',
      suggestions: [],
      getSuggestionsTimeout: null,
    };
  },
  methods: {

    handleLocationReceived(location) {
      this.searchQuery = location;
    },
    getSuggestions() {
      clearTimeout(this.getSuggestionsTimeout);
      this.getSuggestionsTimeout = setTimeout(() => {
        console.log('Getting suggestions for: ' + this.searchQuery);
        this.suggestions = ["test1","test2","test3"]
      }, 500);
    },
  },
  watch: {
    searchQuery() {
      this.getSuggestions();
    }
  }
};
</script>
<style scoped>
.search input {
  margin-right: 10px;
}
</style>