<template>
<div class="sidebar">
	<SidebarHeader />
	<ul id="navigation" class="list list_menu">
		<li v-for="(item, index) in navigation"
			class="list__item list_item_sidebar"
			:key="'item'+index">
			<span v-if="item.subnav"
				class="icon"
				:class="{'icon-open': !item.open,
						'icon-closed': item.open}"></span>
			<div class="text text_menu"
				@click="item.open = !item.open">
				{{ item.title }}
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
		position: relative;
		color: #555;
		border-top: 1px solid #dedede;
		cursor: pointer;
	}

	.dropdown {}
	.dropdown_level_2 {
		padding-left: 20px;
	}

	.text {}
	.text_menu {
		padding: 10px 0;
		text-indent: 20px;
	}

	.icon {
		position: absolute;
		top: 12px;
		right: 10px;
		width: 30px;
		height: 30px;
	}
}
</style>

