<template>
  <div style="width: 316px; color: #6D2080;">
    <label for="filter" class="ml-3">Filtrar por:</label>
    <v-autocomplete
      id="filter"
      :items="items"
      v-model="itemSelected"
      style="margin: 0; padding: 0;"
      placeholder="Escolha uma opção"
    ></v-autocomplete>
  </div>
</template>

<script>
export default {
  name: 'FilterSelector',
  data () {
    return {
      items: ['Região', 'Capital', 'Lingua', 'País', 'Código de ligação'],
      itemSelected: '',
    }
  }
}
</script>

<style>
#filter {
  font-size: 18px;
  padding-left: 25px;
  color: #8D8D8D;
}
</style>
