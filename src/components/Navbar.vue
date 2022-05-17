<template>
  <nav class="main-nav">
    <router-link
      class="main-nav__link main-nav__link--active"
      :to="{ name: 'Home' }"
      >Projects</router-link
    >
    <router-link
      class="main-nav__link main-nav__link--active"
      :to="{ name: 'AddProject' }"
      >New Project</router-link
    >
  </nav>
</template>
<script>
export default {}
</script>

<style lang="scss" scoped >
@import '../assets/global.scss';

.main-nav {
  text-align: center;
  margin: 40px auto;
}
.main-nav__link {
  display: inline-block;
  text-decoration: none;
  background-color: $accent-color;
  padding: 10px;
  border-radius: 10px;
  margin: 0 10px;
  color: $font-color;
  font-size: 20px;
  letter-spacing: 1px;
}
.router-link-active {
  border: 2px solid $done;
  
}
</style>
