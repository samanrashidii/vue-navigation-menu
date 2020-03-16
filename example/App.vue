<template>
  <div id="app">
    <VueNavigationMenu :items="items" />asd
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
