<template>
  <div class="d-flex">
    <v-img
      lazy-src="https://picsum.photos/id/11/10/6"
      max-height="258"
      max-width="443"
      src="https://picsum.photos/id/11/500/300"
    ></v-img>
    <div class="info">
      <span>Nome: Brasil</span>
      <span>Capital: Brasília</span>
      <span>Região: <NuxtLink to="/">Região</NuxtLink></span>
      <span>Sub-região: Sub-região</span>
      <span>População: XXXXXX</span>
      <span>Linguas: Português</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CountryInfo'
}
</script>

<style scoped>
.info {
  min-width: 213px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  background: #fff !important;
  color: #454545;
  margin-left: 24px;
}
</style>
