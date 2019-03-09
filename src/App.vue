<template>
  <div id="app">
    <Index msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
  import Index from './components/index.vue'

  export default {
    name: 'app',
    components: {
      Index
    }
  }
</script>

<style>
  body {
    padding: 0;
    margin: 0;
  }
</style>