<template>
	<div class="_root">
		<theme-controller ref="themeController" />
		<title-bar title="Axeri" />

		<nav-bar logo="Axeri" :links="[
			{
				href: '/',
				label: 'Home'
			},
			{
				href: '/about',
				label: 'About'
			}
		]" />

		<div class="page">
			<div class="content">
				<router-view />
			</div>

			<div class="footer">
				<Footer />
			</div>
		</div>
	</div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Ref } from "vue-property-decorator";

export default class Main extends Vue {
	@Ref("themeController") theme!: { loadTheme(name: any): {} };

	public mounted() {
		this.theme.loadTheme("Dark");
	}
}
</script>

<style lang="less" scoped>
._root {
	display: flex;
	flex-direction: column;
	width: 100vw;
	height: 100vh;

	.page {
		height: calc(100% - 40px);
		display: flex;
		width: 100vw;
		overflow: auto;
		flex-direction: column;

		.content {
			min-height: calc(100% - 40px);
		}
	}
}
</style>