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
      v-bind:class="{ completed: current === 'completed' }"
    >
      Completed
    </button>
    <button
      @click="updateFilter('inProgress')"
      class="filter-nav__button filter-nav__button--inProgress"
      v-bind:class="{ inProgress: current === 'inProgress' }"
    >
      In progress
    </button>
  </nav>
</template>
<script>
export default {
  props: ["current"],
  methods: {
    updateFilter(filter) {
      this.$emit("filterChange", filter)
    },
  },
}
</script>

<style lang="scss">
@import '../assets/global.scss';

.filter-nav__button {
  background-color: $accent-color;
  color: $font-color-not-active;
  outline: none;
  font-size: 12px;
  text-transform: uppercase;
  padding: 10px;
  margin-right: 10px;
  letter-spacing: 1px;
  font-weight: bold;
  border: 1px solid #999;
  border-radius: 10px;
  cursor: pointer;
}

.active {
  color: $font-color;
}

.inProgress {
  color: $font-color;
  border: 1px solid $notDone;
}

.completed {
  color: $font-color;
  border: 1px solid $done;
}
</style>
