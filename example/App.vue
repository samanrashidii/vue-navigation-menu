<template>
  <div id="app">
    <VueNavigationMenu />
  </div>
</template>

<script>
// For test built file
// import VueNavigationMenu from '../lib/vue-navigation-menu.min.js'

// For test local
import VueNavigationMenu from '../src/index'

export default {
  name: 'App',
  data () {
    return {
      value: ''
    }
  },
  components: {
    VueNavigationMenu
  }
}
</script>
