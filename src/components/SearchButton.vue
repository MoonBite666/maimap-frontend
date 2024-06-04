<script setup>

</script>

<template>
  <button @click="search">查询</button>
</template>

<script>
export default {
  props:{
    query: String,
  },
  methods: {
    search() {
      console.log('Searching for: ' + this.query);
    },
  },
};
</script>

<style scoped>

</style>