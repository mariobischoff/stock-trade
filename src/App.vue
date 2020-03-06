<template>
  <v-app>
    <AppHeader />
    <v-content>
      <transition
        mode="out-in"
        enter-active-class="animated fadeInUp faster"
        leave-active-class="animated fadeOutDown faster"
      >
        <router-view />
      </transition>
    </v-content>
  </v-app>
</template>

<script>
import AppHeader from '@/components/base/AppHeader'

export default {
  components: {
    AppHeader
  },
  created () {
    this.$store.dispatch('initStocks')
  }
}
</script>
<style>
.trader {
  font-weight: 100
}

</style>