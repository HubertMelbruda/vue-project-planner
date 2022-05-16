<template>
  <form @submit.prevent="handelSumbit" class="form">
    <label class="form__label">Title</label>
    <input type="text" required v-model="title" class="form__input" />
    <label class="form__label">Details:</label>
    <textarea
      name="details"
      cols="30"
      rows="10"
      v-model="details"
      class="form__textarea"
    ></textarea>
    <button class="form_button">Update Project</button>
  </form>
</template>

<script>
const axios = require('axios')

export default {
  props: ['id'],
  data() {
    return {
      title: '',
      details: '',
      uri: 'http://localhost:8000/projects/' + this.id
    }
  }, 
  mounted() {
    axios
      .get(this.uri)
      .then(res => {
        this.title = res.data.title
        this.details = res.data.details
      })
      .catch(err => console.log(err))
  },
  methods: {
    handelSumbit() {
      let project = {
        title: this.title,
        details: this.details,
      }
      axios
        .patch(this.uri, project)
        .then(() => this.$router.push({ name: 'Home'}))
        .catch(err => console.log(err))
    }
  }
}
</script>

<style lang="scss">
.form {
  background: white;
  padding: 20px;
  border-radius: 10px;
}
.form__label {
  display: block;
  color: #bbb;
  text-transform: uppercase;
  font-size: 16px;
  font-weight: bold;
  letter-spacing: 1px;
  margin: 20px 0 10px 0;
}
.form__input {
  padding: 10px;
  border: 0;
  border-bottom: 1px solid #ddd;
  width: 100%;
  box-sizing: border-box;
}
.form__textarea {
  border: 1px solid #ddd;
  padding: 10px;
  width: 100%;
  box-sizing: border-box;
  height: 100px;
}
.form_button {
  display: block;
  margin: 20px auto 0;
  background: #00ce89;
  color: white;
  padding: 10px;
  border: 0;
  border-radius: 6px;
  font-size: 16px;
}
</style>