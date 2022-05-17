<template>
  <div class="project" :class="{ complete: project.complete }">
    <div class="project__details">
      <h3 @click="handleShowDetails" class="project__title">
        {{ project.title }}
      </h3>
      <div class="project__icons">
        <router-link :to="{ name: 'EditProject', params: { id: this.project.id}}">
          <span @click="handleEditProject" class="material-icons"> edit </span>
        </router-link>
        <span @click="handleDeleteProject" class="material-icons">
          delete
        </span>
        <span @click="toggleComplete" class="material-icons project__icons--done"> done </span>
      </div>
    </div>
    <div v-if="showDetails" class="project__details">
      <p>{{ project.details }}</p>
    </div>
  </div>
</template>

<script>
const axios = require("axios")

export default {
  props: ["project"],
  data() {
    return {
      showDetails: false,
      uri: "http://localhost:8000/projects/" + this.project.id,
    }
  },
  methods: {
    handleShowDetails() {
      this.showDetails = !this.showDetails
    },
    handleDeleteProject() {
      axios
        .delete(this.uri)
        .then(() => this.$emit("deleteProject", this.project.id))
        .catch(err => console.log(err))
    },
    toggleComplete() {
      axios
        .patch(this.uri, { complete: !this.project.complete })
        .then(() => this.$emit("complete", this.project.id))
        .catch(err => console.log(err))
    },
  },
}
</script>
<style lang="scss" scoped>
@import '../assets/global.scss';

.project {
  margin: 20px auto;
  background: $accent-color;
  padding: 10px 20px;
  border-radius: 4px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.411);
  border-left: 4px solid $notDone;
  letter-spacing: 0.5px;
}

.complete {
  border-left: 4px solid $done;

  .project__icons--done {
    color: $done;
  }
}

.project__details {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.project__title {
  cursor: pointer;
}

.material-icons {
  font-size: 24px;
  margin-left: 10px;
  color: $icons-color;
  cursor: pointer;
}

.material-icons:hover {
  color: $icons-color--action;
}
</style>
