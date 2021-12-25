<template>
  <div>
    <v-btn
      elevation="2"
      width="136"
      class="font-weight-regular text-capitalize"
      outlined
      tile
      color="#6D2080"
      @click="toHome"
    >
      <img src="../../assets/icons/ArrowBack.svg" alt="Icon Arrow Left" class="mr-5">
      Voltar
    </v-btn>
  </div>
</template>

<script>
export default {
  name: 'BackButton',
  methods: {
    toHome() {
      this.$router.push({ path: '/' })
    }
  }
}
</script>
