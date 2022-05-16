<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">
        <SingleProject
          :project="project"
          @deleteProject="handleDeleteProject"
          @complete="handleToggleComplete"
        />
      </div>
    </div>
  </div>
</template>

<script>
import SingleProject from "../components/SingleProject.vue"
const axios = require("axios").default

export default {
  name: "HomeView",
  components: {
    SingleProject,
  },
  data() {
    return {
      projects: [],
    }
  },
  methods: {
    handleDeleteProject(id) {
      this.projects = this.projects.filter(project => project.id !== id)
    },
    handleToggleComplete(id) {
      let p = this.projects.find(project => {
        return project.id === id
      })
      p.complete = !p.complete
    },
  },
  mounted() {
    axios.get("http://localhost:8000/projects").then(res => {
      this.projects = res.data
    })
  },
}
</script>
