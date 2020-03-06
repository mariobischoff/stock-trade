<template>
  <v-container>
    <span class="d-flex justify-center display-2 mt-2">Portfólio</span>
    <div class="d-flex flex-wrap justify-center mt-5" v-if="stocks.length > 0">
      <Stock
        portfolio
        v-for="stock in stocks"
        :key="stock.id"
        :stock="stock"
      />
    </div>
    <div v-else>
      <span class="headline d-flex justify-center mt-9">Acesse <v-btn text color="green" to="acoes">Ações</v-btn> para começar a operar</span>
    </div>
  </v-container>
</template>

<script>
import Stock from '../components/Stock'

export default {
  name: 'Portifolio',
  components: {
    Stock
  },
  computed: {
    stocks () {
      return this.$store.getters.stockPortfolio
    }
  }
}
</script>
