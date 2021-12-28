<template>
  <v-card
    class="mb-10"
    style="cursor: pointer;"
    width="316"
    tile
    @click="toCountry()"
  >
    <v-img height="181" :src="card.flag"></v-img>
  </v-card>
</template>

<script>
export default {
  name: 'CountryCard',
  props: {
    card: Object
  },
  methods:{
    toCountry() {
      this.$router.push({ path: `/country/${this.card.alpha2Code}` })
    }
  }
}
</script>
