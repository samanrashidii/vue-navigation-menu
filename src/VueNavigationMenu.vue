<template>
  <div class="vue-navigation-menu">
    <ul>
		<li v-for="(item, index) in items" :key="index">
			<a :href="item.url" >{{ item.value }}</a>
			<ul class="vue-navigation-menu__submenu" v-if="item.submenu && item.submenu.length > 0">
				<li v-for="submenuItem in item.submenu" :key="submenuItem.value">
					<a :href="submenuItem.url" >{{ submenuItem.value }}</a>
				</li>
			</ul>
		</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'vue-navigation-menu',
  props: {
    items: {
		type:Array,
		default: () => [],
		required:true
	}
  }
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
