<template>
  <v-card :loading="loading" class="mb-10" style="cursor: pointer;" width="316">
    <v-img height="181" :src="card.flag"></v-img>
  </v-card>
</template>

<script>
export default {
  name: 'CountryCard',
  props: {
    card: Object
  }
}
</script>
