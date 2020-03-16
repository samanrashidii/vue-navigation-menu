<template>
  <li>
    <a :href="url">{{name}}</a>
      <ul v-if="subMenus.length > 0">
        <Menu 
          v-for="menu in subMenus" 
          :name="menu.name" 
          :url="menu.url" 
          :subMenus="menu['sub-menus']"
          :key="menu.name"
        />
      </ul>
  </li>
</template>
<script>
export default {
  name: 'vue-navigation-submenu',
  props: {
    name: {type:String, required:true},
    url: {type:String, required:true},
    subMenus: {type:Array, required:true}
  }
}
</script>

<style>

</style>
