<template>
  <div class="home">
    <FilterNav @filterChange="currentFilter = $event" :current="currentFilter"/>
    <div v-if="projects.length">
      <div v-for="project in filteredProjects" :key="project.id">
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
import FilterNav from "../components/FilterNav.vue"
const axios = require("axios").default

export default {
  name: "HomeView",
  components: {
    SingleProject,
    FilterNav,
  },
  data() {
    return {
      projects: [],
      currentFilter: 'all',
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
  computed: {
    filteredProjects() {
      if (this.currentFilter === 'completed') {
        return this.projects.filter(project => project.complete)
      } 
      if (this.currentFilter === 'inProgress') {
        return this.projects.filter(project => !project.complete)
      }
      return this.projects
    } 
  },
  mounted() {
    axios.get("http://localhost:8000/projects").then(res => {
      this.projects = res.data
    })
  },
}
</script>
