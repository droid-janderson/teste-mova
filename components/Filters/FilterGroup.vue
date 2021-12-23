<template>
  <div class="d-flex align-center mt-15" style="max-width: 80%;">
    <filter-selector />
    <v-spacer />
    <search-button />
  </div>
</template>

<script>
import FilterSelector from "./Filter.vue"
import SearchButton from "../Buttons/SearchButton.vue"

export default {
  name: 'FilterGroup',

  components: {
    FilterSelector,
    SearchButton,
  }
}
</script>

<style lang="scss" scoped>
</style>
