<template>
  <div class="d-flex">
    <v-img
      lazy-src="https://picsum.photos/id/11/10/6"
      max-height="258"
      max-width="443"
      :src="card.flag"
    ></v-img>
    <div class="info" style="background-color: transparent !important;">
      <span>Nome: {{ card.name }}</span>
      <span>Capital: {{ card.capital }}</span>
      <span
        >Região:
        <span
          @click="toRegion(card.region)"
          style="text-decoration: underline; color: blue; cursor: pointer;"
          >{{ card.region }}</span
        ></span
      >
      <span>Sub-região: {{ card.subregion }} </span>
      <span>População: {{ card.population }}</span>
      <span
        >Linguas:
        <span class="mr-1" v-for="(item, index) in card.languages" :key="index"
          >{{ item.name }};</span
        ></span
      >
    </div>
  </div>
</template>

<script>
export default {
  name: 'CountryInfo',
  props: {
    card: Object
  },

  methods: {
    toRegion (region) {
      this.$router.push({ path: '/', query: { region: region } })
    }
  }
}
</script>

<style scoped>
.info {
  min-width: 213px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  color: #454545;
  margin-left: 24px;
}
</style>
