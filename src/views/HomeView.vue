<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">
        <p>{{ project.title }}</p>
      </div>
    </div>
  </div>
</template>

<script>
const axios = require("axios").default

export default {
  name: "HomeView",
  components: {},
  data() {
    return {
      projects: [],
    }
  },
  mounted() {
    axios.get("http://localhost:8000/projects").then(res => {
      this.projects = res.data
    })
  },
}
</script>
