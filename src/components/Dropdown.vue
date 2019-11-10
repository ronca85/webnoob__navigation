<template>
<ul class="sub-items"
	v-show="list.open">
	<li class="sub-item"
		v-for="(item, index) in list.subnav"
		:key="'item'+index">
		<span v-if="item.subnav"
			class="icon"
			:class="{'icon-open': !item.open,
					'icon-closed': item.open}"></span>
		<div class="title"
			@click="item.open = !item.open">
			{{ item.title }}
		</div>
		<Dropdown class="subnav"
			v-if="item.subnav"
			:list="item" />
	</li>
</ul>
</template>

<script>
export default {
	name: "Dropdown",
	props: [
		"list"
	]
}
</script>

<style lang="scss" scoped>

	.sub-items {
		list-style: none;

		.sub-item {
			position: relative;
			color: #fefefe;
			background-color: #333;
			border-top: 1px solid #222;
			cursor: pointer;

			.subnav {
				padding-left: 20px;
			}

			.title {
				padding: 10px 0;
				text-indent: 20px;
			}

			i {
				position: absolute;
				top: 12px;
				right: 10px;
			}
		}
	}
</style>

