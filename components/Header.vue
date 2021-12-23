<template>
  <v-app-bar :clipped-left="clipped" fixed app height="80">
    <div class="ml-6">
      <NuxtLink to="/"><img
        src="../assets/logo/logo_principal.svg"
        alt="Logo Mova"
        class="mr-4"
      /></NuxtLink>
    </div>
    <filter />
    <v-spacer />
    <back-button class="mr-6"/>
  </v-app-bar>
</template>

<script>
import BackButton from './Buttons/BackButton.vue'

export default {
  name: 'Header',
  components: {
    BackButton
  }
}
</script>
