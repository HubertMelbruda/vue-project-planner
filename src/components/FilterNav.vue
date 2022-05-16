<template>
  <nav class="filter-nav">
    <button
      @click="updateFilter('all')"
      class="filter-nav__button"
      v-bind:class="{ active: current === 'all' }"
    >
      View All
    </button>
    <button
      @click="updateFilter('completed')"
      class="filter-nav__button"
      v-bind:class="{ active: current === 'completed' }"
    >
      Completed
    </button>
    <button
      @click="updateFilter('inProgress')"
      class="filter-nav__button"
      v-bind:class="{ active: current === 'inProgress' }"
    >
      In progress
    </button>
  </nav>
</template>
<script>
export default {
  props: ['current'],
  methods: {
    updateFilter(filter) {
      this.$emit('filterChange', filter)
    }
  }

}
</script>

<style lang="scss" scoped>
.filter-nav__button {
  background: none;
  border: none;
  color: #bbb;
  outline: none;
  font-size: 12px;
  text-transform: uppercase;
  margin-right: 10px;
  letter-spacing: 1px;
  font-weight: bold;
  cursor: pointer;
}

.active {
  color: #555;
}
</style>
