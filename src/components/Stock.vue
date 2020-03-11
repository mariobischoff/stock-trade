<template>
  <v-card
    class="ma-2"
    width="370px"
  >
    <v-toolbar :color="portfolio ? 'primary' : 'green'">
      {{ stock.name }}
      <v-spacer />
      Preço: {{ stock.price | currency }} {{ portfolio ? 'Qnt: ' + stock.quantity : ''}}
    </v-toolbar>
    <v-card-text class="d-flex align-center justify-space-between">
      <v-text-field
        style="max-width: 220px"
        class="mr-2"
        type="number"
        v-model.number="quantity"
        :error="(portfolio ? hasNotQuantity : insufficientFunds) || !Number.isInteger(quantity)"
        :rules="[]"
        label="Quantidade"
      />
      <v-btn
        text
        color="black"
        :disabled="(portfolio ? hasNotQuantity : insufficientFunds) || quantity <= 0 || !Number.isInteger(quantity)"
        @click="fire()"
      >
        {{ portfolio ? 'Vender' : 'Comprar'  }}
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
  },
  computed: {
    funds () {
      return this.$store.getters.funds
    },
    insufficientFunds () {
      return this.quantity * this.stock.price > this.funds
    },
    hasNotQuantity () {
      return this.stock.quantity < this.quantity
    }
  }
}
</script>