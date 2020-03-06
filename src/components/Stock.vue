<template>
  <v-card
    class="ma-2"
    width="350px"
  >
    <v-toolbar :color="portfolio ? 'primary' : 'green'">
      {{ stock.name }}
      <v-spacer />
      Preço: R$ {{ stock.price | currency }} {{ portfolio ? 'Qnt: ' + stock.quantity : ''}}
    </v-toolbar>
    <v-card-text class="d-flex justify-center">
      <v-text-field
        type="number"
        v-model.number="quantity"
        :rules="[]"
        label="Quantidade"
      />
      <v-btn
        text
        color="black"
        :disabled="quantity <= 0 || !Number.isInteger(quantity)"
        @click="fire()"
      >
        {{ portfolio ? 'Vender' : 'Comprar' }}
      </v-btn>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      quantity: 0
    }
  },
  props: {
    stock: {
      type: Object,
      required: true
    },
    portfolio: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    fire () {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      }
      if (this.portfolio) {
        this.$store.dispatch('sellStock', order)
      } else {
        this.$store.dispatch('buyStock', order)
      }
      this.quantity = 0
    }
  }
}
</script>