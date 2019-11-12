<template>
<div class="sidebar">
	<SidebarHeader />
	<ul id="navigation" class="list list_menu">
		<li v-for="(item, index) in navigation"
			class="list__item list_item_sidebar"
			:key="'item'+index">
			<div class="shell posrel">
				<a :href="item.title" class="link link_menu">
					{{ item.title }}
				</a>
				<span v-if="item.subnav"
					class="icon"
					@click="item.open = !item.open"
					:class="{'icon-open': !item.open,
							'icon-closed': item.open}">
					<svg class="svg svg_icon" viewBox="0 0 50 50">
						<rect class="transform_origin_center scales_y transition_primary" width="2" height="20" x="24" y="15"></rect>
						<rect class="" width="20" height="2" x="15" y="24"></rect>
					</svg>
				</span>
			</div>
			<Dropdown class="dropdown"
				v-if="item.subnav"
				:list="item" />
		</li>
	</ul>
</div>
</template>

<script>
	import SidebarHeader from './SidebarHeader'
	import Dropdown from './Dropdown'
	export default {
		computed: {
			navigation() {
				// console.log("this", this.$store);
				return this.$store.getters.navigation;
			}
		},
		components: {
			SidebarHeader,
			Dropdown,
		}
	}
</script>

<style lang="scss" scoped>
.posrel {
	position: relative;
}
.transform_origin_center {
	transform-origin: center;
}
.transition_primary {
	transition: .28s ease-in-out;
}

.sidebar {
	width: 100%;
	max-width: 350px;
	min-height: 100vh;
	background-color: #fefefe;
	box-shadow: 10px 0 20px rgba($color: #000, $alpha: .2)
}

#navigation {
	padding: 0;
	list-style: none;
	border-bottom: 1px solid #dedede;
	
	.list {
		list-style: none;
	}
	.list_menu {}

	.list__item {}
	.list_item_sidebar {
		color: #555;
		border-top: 1px solid #dedede;
	}

	.dropdown {}
	.dropdown_level_2 {
		padding-left: 20px;
	}

	.link {}
	.link_menu {
		padding: 10px 0;
		text-indent: 20px;
		display: block;
		color: #000;
	}

	.icon {
		cursor: pointer;
		position: absolute;
		top: 0;
		right: 0;
		height: 100%;
		display: block;
		background-color: #39df5f;
		width: 40px;
	}
	.icon-open {
		background-color: #df0489;
		.scales_y {
			transform: scaleY(0);
		}
	}
	.icon-closed {
		background-color: #dbcf5d;
	}
}
</style>

