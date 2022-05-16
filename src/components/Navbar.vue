<template>
  <nav class="main-nav">
    <router-link class="main-nav__link main-nav__link--active" :to="{ name: 'Home'}">Projects</router-link>
    <router-link class="main-nav__link main-nav__link--active" :to="{ name: 'AddProject'}">Add a New Project</router-link>
  </nav>
</template>
<script>
export default {
  
}
</script>
<style lang="scss" scoped>
  .main-nav {
    text-align: center;
    margin: 40px auto;
  }
  .main-nav__link {
    display: inline-block;
    text-decoration: none;
    margin: 0 10px;
    color: #999;
    font-size: 20px;
  }
  a.router-link-active {
    border-bottom: 2px solid #00ce89;
    padding-bottom: 4px;
  }
</style>