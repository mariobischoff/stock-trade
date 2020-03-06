<template>
  <v-app-bar
    app
    color="grey lighten-4"
  >
    <!-- TITLE -->
    <v-toolbar-title>
      <router-link to="/" tag="span" style="cursor: pointer">
        <span class="font-weight-bold">STOCK</span>
        <span class="font-weight-light">TRADER</span>
      </router-link>
    </v-toolbar-title>

    <!-- MENUITEMS -->
    <v-toolbar-items class="ml-8" v-model="menuItems">
      <v-btn
        text
        v-for="(menu, i) in menuItems"
        :key="i"
        router
        :to="menu.path"
      >
        {{ menu.name }}
      </v-btn>
    </v-toolbar-items>

    <v-spacer></v-spacer>

    <v-toolbar-items>
      <v-btn
        text
        @click="newDay"
      >
        FINALIZAR DIA
      </v-btn>


      <v-menu bottom offset-y>
        <template v-slot:activator="{ on }">
          <v-btn
            text
            v-on="on"
          >
            CARREGAR & SALVAR
          </v-btn>
        </template>

        <v-list>
          <v-list-item
            @click="saveData"
          >
            <v-list-item-title>Salvar Dados</v-list-item-title>
          </v-list-item>
          <v-list-item
            @click="loadData"
          >
            <v-list-item-title>Carregar Dados</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>



    </v-toolbar-items>
    <span class="font-weight-regular">Saldo: R$ {{ funds | currency }}</span>
  </v-app-bar>
</template>

<script>
export default {
  name: 'AppHeader',
  data () {
    return {
      bottomNav: 'recent',
      menuItems: [
        { name: 'Inicio', path: '/'},
        { name: 'Portifólio', path: '/portifolio'},
        { name: 'Ações', path: '/acoes'}

      ]
    }
  },
  methods: {
    newDay () {
      this.$store.dispatch('changePrice')
    },
    loadData () {
      this.$$store.dispatch('loadData')
    },
    saveData () {
      this.$store.dispatch('saveData')
    }
  },
  computed: {
    funds () {
      return this.$store.state.portfolio.funds
    }
  }
}
</script>

<style>
</style>