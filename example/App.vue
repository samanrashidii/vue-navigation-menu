<template>
  <div id="app">
    <div class="nav-wrapper">
      <VueNavigationMenu :items="items" />
    </div>
  </div>
</template>

<script>
// For test built file
// import VueNavigationMenu from '../lib/vue-navigation-menu.min.js'

// For test local
import Data from "./data.json"
import VueNavigationMenu from '../src/VueNavigationMenu.vue'

export default {
  name: 'App',
  data () {
    return {
      items: Data
    }
  },
  components: {
    VueNavigationMenu
  }
}
</script>

<style scoped>

.nav-wrapper {
  position: fixed;
  top:0;
  left: 0;
  width:100%;
  z-index: 99;
}

</style>