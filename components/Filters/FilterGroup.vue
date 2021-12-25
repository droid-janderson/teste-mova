<template>
  <div class="d-flex align-center mt-15" style="max-width: 80%;">
    <div style="width: 316px; color: #6D2080;">
      <label for="filter" class="ml-3">Filtrar por:</label>
      <v-autocomplete
        id="filter"
        :items="items"
        v-model="select"
        style="margin: 0; padding: 0;"
        placeholder="Escolha uma opção"
      ></v-autocomplete>
    </div>
    <v-spacer />
    <div v-if="select" style="width: 316px; color: #6D2080;">
      <label for="filterPerItem" class="ml-3">Itens</label>
      <v-autocomplete
        id="filterPerItem"
        :items="itemsName"
        v-model="selectName"
        style="margin: 0; padding: 0;"
        placeholder="Escolha uma opção"
      ></v-autocomplete>
    </div>
    <v-spacer />
    <v-btn
      width="156px"
      elevation="2"
      color="#6D2080"
      style="color: #fff; font-weight: 400; border-radius: 10px;"
      @click="getCountry()"
      >Pesquisar</v-btn
    >
    <!-- $emit('getCountry', this.selected, this.selectName) -->
  </div>
</template>

<script>
export default {
  name: 'FilterGroup',
  data () {
    return {
      items: ['Região', 'Capital', 'Lingua', 'País', 'Código de ligação'],
      select: null,
      selected: null,
      selectName: null,
      cards: []
    }
  },

  emits: ['getCountry'],

  async mounted () {
    await this.getRegion()
  },
  methods: {
    async getRegion () {
      try {
        const response = await this.$axios.$get('/all')

        this.cards = response
      } catch (error) {
        throw new Error(error)
      }
    },

    getCountry () {
      this.$emit('getCountry', this.selected, this.selectName)
    }
  },

  computed: {
    itemsName () {
      let select = this.select
      let arrayNames = []

      this.cards.map(item => {
        if (select == 'Região') {
          arrayNames.push(item.region)
          this.selected = 'region'
        } else if (select == 'Capital') {
          if (item.capital) {
            arrayNames.push(item.capital)
          }
          this.selected = 'capital'
        } else if (select == 'Lingua') {
          arrayNames.push(item.languages[0].name)
          this.selected = 'lang'
          this.selectedLang = item.languages
        } else if (select == 'País') {
          arrayNames.push(item.name)
          this.selected = 'name'
        } else if (select == 'Código de ligação') {
          arrayNames.push(item.callingCodes[0])
          this.selected = 'callingcode'
        }
      })

      return arrayNames
    }
  }
}
</script>

<style>
#filter,
#filterPerItem {
  font-size: 18px;
  padding-left: 25px;
  color: #8d8d8d;
}
</style>
