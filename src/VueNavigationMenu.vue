<template>
  <nav class="vue-navigation-menu">
    <ul>
		<li v-for="(item, index) in items" :key="index">
			<a href="#" @click.prevent="itemClicked(item.url)">
				<Icon name="beer" />
				<span>{{ item.value }}</span>
			</a>
			<ul class="vue-navigation-menu__submenu" v-if="item.submenu && item.submenu.length > 0">
				<li v-for="submenuItem in item.submenu" :key="submenuItem.value">
					<a href="#" @click.prevent="itemClicked(submenuItem.url)">{{ submenuItem.value }}</a>
				</li>
			</ul>
		</li>
    </ul>
  </nav>
</template>
<script>
import 'vue-awesome/icons';
import Icon from 'vue-awesome/components/Icon';
export default {
  name: 'vue-navigation-menu',
  components: {
	Icon
  },
  props: {
    items: {
		type:Array,
		default: () => [],
		required:true
	}
  },
  methods: {
	itemClicked (url) {
		this.$emit('itemClicked', url)
	}
  }
}
</script>

<style lang="scss">
// Varibales
$dark: #212529;
$darker: #1a1d20;
$white: #f8f9fa;

.vue-navigation-menu {
  width:100%;
  background-color: $dark;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  ul{
	display:flex;
	flex-direction: row;
	padding:0;
	margin:0;
	list-style:none;
	li{
		a{
			display:block;
			font-size: 13px;
			color: $white;
			outline: none;
			text-decoration: none;
			padding:13px 20px;
			transition: all .2s ease-in-out;
			&:hover{
				background-color: $darker;
			}
		}
		ul{
			display:none;
			li{
				a{

				}
			}
		}
	}
  }
}
</style>
