<template>
  <Navbar />
  <router-view/>
</template>

<script>
import Navbar from './components/Navbar.vue'
export default {
  components: {
    Navbar,
  }
  
}
</script>

<style lang='scss'>
@import 'assets/global.scss';

body {
  background: $prime-color;
}

#app {
  font-family: "Quicksand", "Roboto", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: $font-color;
}
</style>
