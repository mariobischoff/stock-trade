<template>
  <v-container>
    <h1 class="display-3 font-weight-light my-6">Negocie e Consulte suas Ações</h1>
    <v-sheet elevation="6">
      <v-alert dense class="mt-6" type="info">
        Você pode Salvar & Carregar os Dados
      </v-alert>
    </v-sheet>
    <v-sheet elevation="6">
      <v-alert dense type="info" color="success">
        Clique em 'Finalizar Dia' para iniciar um novo dia!
      </v-alert>
    </v-sheet>
    <v-divider></v-divider>
    <h2 class="display-1 mt-4">Seu Saldo: {{ funds | currency }}</h2>
  </v-container>
</template>

<script>
export default {
  name: 'Inicio',
  computed: {
    funds () {
      return this.$store.getters.funds
    }
  },
  components: {
  }
}
</script>
