<template>
  <v-container>
      <span class="d-flex justify-center display-3 font-wight-light mt-2">Ações</span>
      <div class="d-flex flex-wrap justify-center mt-5">
        <stock
          v-for="stock in stocks"
          :key="stock.id"
          :stock="stock"
        />
      </div>
  </v-container>
</template>

<script>
import Stock from '../components/Stock'
export default {
  name: 'Acoes',
  components: { Stock },
  computed: {
    stocks () {
      return this.$store.getters.stocks
    }
  }
}
</script>
