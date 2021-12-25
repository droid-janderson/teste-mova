<template>
  <div class="mt-10">
    <country-info class="mb-16" :card="country" />
    <span style="font-size: 18px;">Países Vizinhos</span>
    <!-- <div class="container-cards">
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
    </div> -->
  </div>
</template>

<script>
import CountryCard from '../../components/Country/CountryCard.vue'
import CountryInfo from '../../components/Country/CountryInfo.vue'
export default {
  components: { CountryInfo, CountryCard },

  data () {
    return {
      name: this.$route.params.name,
      pagination: {
        page: 1,
        total: 0,
        perPage: 3,
        visible: 7
      },
      country: {},
    }
  },

  async mounted () {
    await this.getCountry()
  },
  methods: {
    async getCountry () {
      try {
        const response = await this.$axios.$get(`/alpha/${this.name}`)

        this.country = response
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
