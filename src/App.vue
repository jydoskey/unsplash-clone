<template>
  <div id="app">
    <Landing />
  </div>
</template>

<script>
  import Landing from './components/Landing.vue'

  export default {
    name: 'App',
    components: {
      Landing
    }
  }
</script>

<style lang="scss">
  @import "@/scss/themed-bootstrap.scss";

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
  }

  html {
    font-size: 14px;
  }
</style>