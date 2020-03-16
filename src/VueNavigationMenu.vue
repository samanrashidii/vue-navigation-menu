<template>
  <nav class="vue-navigation-menu" :class="variant">
    <ul>
		<li v-for="(item, index) in items" :key="index">
			<a href="#" @click.prevent="itemClicked(item.url)">
				<Icon v-if="item.icon" :name="item.icon" />
				<span>{{ item.value }}</span>
			</a>
			<ul class="vue-navigation-menu__submenu" v-if="item.submenu && item.submenu.length > 0">
				<li v-for="submenuItem in item.submenu" :key="submenuItem.value">
					<a href="#" @click.prevent="itemClicked(submenuItem.url)">
						<Icon v-if="item.icon" :name="item.icon" />
						<span>{{ submenuItem.value }}</span>
					</a>
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
		type: Array,
		default: () => [],
		required:true
	},
	variant: {
		type: String,
		default: 'dark',
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
$grey: #dadada;

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
			display:flex;
			font-size: 13px;
			outline: none;
			text-decoration: none;
			padding:13px 20px;
			transition: all .2s ease-in-out;
			svg{
				width: 12px;
				height: 14px;
				margin-right:5px;
			}
		}
		ul{
			display:none;
		}
	}
  }
  &.dark{
	ul li a{
		color: $white;
		background-color: $dark;
		&:hover{
			color:$grey;
			background-color: $darker;
		}
	}
  }
}
</style>
