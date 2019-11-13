<template>
<ul class="list list_menu list_menu_level_2 bg_dark"
	v-show="list.open">
	<li class="list__item list_item_sidebar"
		v-for="(item, index) in list.subnav"
		:key="'item'+index">
		<div class="shell posrel d_flex align_items_center justify_content_space_between padding_10">
			<a :href=item.title class="link link_menu color_light d_flex align_items_center">
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
		<Accordion class="accordion accordion_level_2"
			v-if="item.subnav"
			:list="item" />
	</li>
</ul>
</template>

<script>
export default {
	name: "Accordion",
	props: [
		"list"
	]
}
</script>

<style lang="scss" >
.list {
	list-style: none;
	padding-left: 0;
}
.list_menu {}
.list_menu_level_2 {
	border-top: 1px solid #888;
}

.list__item {
	position: relative;
}

.shell {}

.accordion {}
.accordion_level_2 {
	padding-left: 20px;
}

.link {}
.link_menu {
	min-height: 40px;
}

.icon {
	cursor: pointer;
	background-color: #39df5f;
}
.icon_accordion_toggle {
	min-width: 40px;
	max-width: 40px;
	background-color: #999;
}
.icon-open {
	// background-color: #dbcf5d;
	.scales_y {
		transform: scaleY(0);
	}
}
.icon-closed {
	// background-color: #df0489;
}
//
// modifiers
//
.w100 {
	width: 100%;
}
.h100 {
	height: 100%;
}
.posrel {
	position: relative;
}
.d_flex {
	display: flex;
}
.justify_content_space_between {
	justify-content: space-between;
}
.justify_content_center {
	justify-content: center;
}
.align_items_center {
	align-items: center;
}
.padding_10 {
	padding: 10px;
}
.rounded_9999 {
	border-radius: 9999px;
}
.bg_dark {
	background-color: #333;
}
.color_light {
	color: #fff;
}
.color_dark {
	color: #000;
}

.transform_origin_center {
	transform-origin: center;
}
.transition_primary {
	transition: .28s ease-in-out;
}

</style>

