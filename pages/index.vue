<template>
  <div>
    <filter-group @getCountry="getData" />
    <div class="container-cards">
      <country-card
        v-for="card in paginatedItems"
        :key="card.name"
        :card="card"
      />
    </div>
    <div class="container-pagination">
      <v-pagination
        class="pagination"
        color="#6D2080"
        v-model="pagination.page"
        :length="pagination.total"
        :total-visible="pagination.visible"
      ></v-pagination>
    </div>
  </div>
</template>

<script>
import CountryCard from '../components/Country/CountryCard.vue'
import FilterGroup from '../components/Filters/FilterGroup.vue'

export default {
  name: 'IndexPage',
  data () {
    return {
      cards: [],
      pagination: {
        page: 1,
        total: 0,
        perPage: 10,
        visible: 7
      }
    }
  },
  components: {
    FilterGroup,
    CountryCard
  },

  async mounted () {
    await this.getAll()
  },
  methods: {
    async getAll () {
      try {
        const response = await this.$axios.$get('/all')

        this.cards = response
        this.pagination.total = Math.ceil(
          this.cards.length / this.pagination.perPage
        )
      } catch (error) {
        throw new Error(error)
      }
    },
    async getData (selected ,selectName) {
      try {
        const response = await this.$axios.$get(`/${selected}/${selectName}`)

        this.cards = null
        this.cards = response
        this.pagination.total = Math.ceil(
          this.cards.length / this.pagination.perPage
        )
      } catch (error) {
        throw new Error(error)
      }
    }
  },
  computed: {
    paginatedItems () {
      let page = this.pagination.page - 1
      const perPage = this.pagination.perPage
      let start = page * perPage
      let end = start + perPage

      const paginatedItems = this.cards

      return paginatedItems.slice(start, end)
    }
  }
}
</script>

<style scoped>
.container-cards {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  max-width: 100%;
  margin-top: 40px;
}

.container-pagination {
  width: 100%;
  display: flex;
  justify-content: center;
}

.pagination {
  position: fixed;
  bottom: 0;
  margin-bottom: 20px;
}
</style>
