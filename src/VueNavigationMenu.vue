<template>
  <div>
    <ul>
      <VueNavigationSubMenu 
        v-for="menu in data" 
        :name="menu.name" 
        :url="menu.url" 
        :subMenus="menu['sub-menus']"
		:key="menu.name"
	/>
    </ul>
  </div>
</template>
<script>
import Data from "../example/data.json"
import VueNavigationSubMenu from './VueNavigationSubMenu.vue'
export default {
  name: 'vue-navigation-menu',
  components: {
	VueNavigationSubMenu
  },
  data () {
	return {
		data: Data
	}
  },
//   props: {
//     menus: {type:Array, required:true}
//   }
}
</script>

<style>
.vue-navigation-menu {
  position: fixed;
  top:0;
  left: 0;
  width:100%;
  background-color: #212529;
  z-index: 99;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.vue-navigation-menu ul{
  padding:0;
  margin:0;
  list-style:none;
}

.vue-navigation-menu a{
  color: #f8f9fa;
  outline: none;
  text-decoration: none;
}
</style>
