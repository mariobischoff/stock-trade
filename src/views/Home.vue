<template>
  <v-container>
    <h1 class="display-2 my-6">Negocie e Consulte suas Ações</h1>
    <v-alert dense class="mt-6" type="info">
      Você pode Salvar & Carregar os Dados
    </v-alert>
    <v-alert dense type="info" color="success">
      Clique em 'Finalizar Dia' para iniciar um novo dia!
    </v-alert>
    <v-divider></v-divider>
    <h2 class="display-1 mt-4">Seu Saldo: R$ {{ funds | currency }}</h2>
  </v-container>
</template>

<script>
export default {
  name: 'Inicio',
  computed: {
    funds () {
      return this.$store.state.portfolio.funds
    }
  },
  components: {
  }
}
</script>
