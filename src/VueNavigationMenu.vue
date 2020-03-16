<template>
  <div>
    Vue Navigation Menu Component
  </div>
</template>
<script>
export default {
  name: 'vue-navigation-menu',
  data () {
    return {
      value: ''
    }
  },
  props: {
    data: {
      type: Array,
      default: null
    },
    direction: {
      type: String,
      default: 'ltr'
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
