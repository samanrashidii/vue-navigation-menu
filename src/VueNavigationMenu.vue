<template>
  <nav
  class="vue-navigation-menu"
  :class="[`vue-navigation-menu--${variant}`, `vue-navigation-menu--icon-${iconVariant}`, {'vue-navigation-menu--vertical': vertical}]"
  >
    <ul>
		<li v-for="(item, index) in items" :key="index" :class="{'has-submenu': item.submenu}" @mouseenter="hoverMenu($event, true)" @mouseleave="hoverMenu($event, false)">
			<a href="#" @click.prevent="itemClicked(item.url)">
				<Icon v-if="item.icon" :name="item.icon" />
				<span>{{ item.value }}</span>
				<Icon v-if="item.submenu && item.submenu.length > 0" name="caret-down" class="submenu-arrow" />
			</a>
			<ul class="vue-navigation-menu__submenu" v-if="item.submenu && item.submenu.length > 0">
				<li v-for="submenuItem in item.submenu" :key="submenuItem.value" :class="{'has-submenu': submenuItem.submenu}" @mouseenter="hoverMenu($event, true)" @mouseleave="hoverMenu($event, false)">
					<a href="#" @click.prevent="itemClicked(submenuItem.url)">
						<Icon v-if="submenuItem.icon" :name="submenuItem.icon" />
						<span>{{ submenuItem.value }}</span>
						<Icon v-if="submenuItem.submenu && submenuItem.submenu.length > 0" name="caret-right" class="submenu-arrow" />
					</a>
					<ul class="vue-navigation-menu__submenu" v-if="submenuItem.submenu && submenuItem.submenu.length > 0">
						<li v-for="innerSubmenu in submenuItem.submenu" :key="innerSubmenu.value">
							<a href="#" @click.prevent="itemClicked(innerSubmenu.url)">
								<Icon v-if="innerSubmenu.icon" :name="innerSubmenu.icon" />
								<span>{{ innerSubmenu.value }}</span>
							</a>
						</li>
					</ul>
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
		default: 'dark'
	},
	iconVariant: {
		type: String,
		default: 'default'
	},
	type: {
		type: Boolean,
		default: false
	},
	vertical: {
		type: Boolean,
		default: false
	}
  },
  methods: {
	itemClicked (url) {
		this.$emit('itemClicked', url)
	},
	hoverMenu (e, val) {
		if (!this.vertical && e.target.className.includes('has-submenu')) {
			val ? e.target.classList.add('vue-navigation-menu--hovered') : e.target.classList.remove('vue-navigation-menu--hovered')
		}
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
$fontsize-sm: 13px;
$fontsize-xs: 11px;
$transition: all .2s ease-in-out;
$submenu-min-width: 150px;
$vertical-width: 300px;

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
			font-size: $fontsize-sm;
			outline: none;
			text-decoration: none;
			padding:13px 20px;
			transition: $transition;
			svg{
				width: 12px;
				height: 14px;
				color: inherit;
				margin-right:5px;
				&.submenu-arrow{
					margin-right: 0;
					margin-left: 5px;
				}
			}
		}
		.vue-navigation-menu__submenu{
			position: absolute;
			min-width: $submenu-min-width;
			opacity: 0;
			visibility: hidden;
			flex-direction: column;
			border-top:1px solid transparent;
			border-radius: 0 0 4px 4px;
			z-index: 99;
			transition: $transition;
			li{
				a{
					font-size: $fontsize-xs;
					svg{
						width: 10px;
						height: 12px;
						margin-right:8px;
						&.submenu-arrow{
							margin-right: 0;
							margin-left: 8px;
						}
					}
				}
				.vue-navigation-menu__submenu{
					top:-1px;
					left: calc(100% - 1px);
					border-top:none;
					border-left:1px solid transparent;
				}
			}
		}
		&.vue-navigation-menu--hovered{
			> .vue-navigation-menu__submenu {
				opacity: 1;
				visibility: visible;
			}
		}
	}
  }
  &.vue-navigation-menu--dark{
	ul li{
		a{
			color: $white;
			background-color: $dark;
			&:hover{
				color:$grey;
				background-color: $darker;
			}
		}
		.vue-navigation-menu__submenu{
			border-color: $darker !important;
		}
	}
  }
  &.vue-navigation-menu--icon-light{
	ul li a svg{
		color: $white;
		&:hover{
			color:$grey;
		}
	}
  }
  &.vue-navigation-menu--icon-dark{
	ul li a svg{
		color: $dark;
		&:hover{
			color:$darker;
		}
	}
  }
  &.vue-navigation-menu--vertical{
	max-width: $vertical-width;
	min-height: 100vh;
	height: 100%;
	ul{
		flex-direction: column;
		li{
			.vue-navigation-menu__submenu{
				position: relative;
				opacity: 1;
				visibility: visible;
				padding-left: 15px;
				border-top:none;
			}
		}
	}
  }
}
</style>
