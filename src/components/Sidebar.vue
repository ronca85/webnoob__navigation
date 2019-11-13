<template>
<div class="sidebar">
	<SidebarHeader />
	<ul id="navigation" class="list list_menu">
		<li v-for="(item, index) in navigation"
			class="list__item list_item_sidebar"
			:key="'item'+index">
			<div class="shell posrel d_flex align_items_center justify_content_space_between padding_10">
				<a :href="item.title" class="link link_menu color_dark d_flex align_items_center">
					{{ item.title }}
				</a>
				<span v-if="item.subnav"
					class="icon icon_accordion_toggle d_flex rounded_9999"
					@click="item.open = !item.open"
					:class="{'icon-closed': !item.open,
							'icon-open': item.open}">
					<svg class="svg svg_icon w100 h100" viewBox="0 0 50 50">
						<rect class="transform_origin_center scales_y transition_primary" width="2" height="20" x="24" y="15"></rect>
						<rect class="" width="20" height="2" x="15" y="24"></rect>
					</svg>
				</span>
			</div>
			<Accordion class="accordion"
				v-if="item.subnav"
				:list="item" />
		</li>
	</ul>
</div>
</template>

<script>
	import SidebarHeader from './SidebarHeader'
	import Accordion from './Accordion'
	export default {
		computed: {
			navigation() {
				// console.log("this", this.$store);
				return this.$store.getters.navigation;
			}
		},
		components: {
			SidebarHeader,
			Accordion,
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
</style>

