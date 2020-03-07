<template>
  <v-container>
    <h1 class="d-flex justify-center display-3 font-weight-light mt-2">Portfólio</h1>
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
import { mapGetters } from 'vuex'

import Stock from '../components/Stock'

export default {
  name: 'Portifolio',
  components: {
    Stock
  },
  computed: {
    ...mapGetters({
      stocks: 'stockPortfolio'
    })
  }
}
</script>
