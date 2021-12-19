<template>
  <v-app-bar :clipped-left="clipped" fixed app height="100">
    <div class="ml-6">
      <img
        src="../assets/logo/logo_principal.svg"
        alt="Logo Mova"
        class="mr-4"
      />
    </div>
    <v-spacer />
    <back-button class="mr-6"/>
  </v-app-bar>
</template>

<script>
import BackButton from './BackButton.vue'

export default {
  name: 'Header',
  components: {
    BackButton
  }
}
</script>
