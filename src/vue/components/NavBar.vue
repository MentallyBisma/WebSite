<template>
	<div class="root">
		<router-link to="/" class="logo">{{ logo }}</router-link>

		<div class="links">
			<router-link :to="link.href" v-for="link in links">{{ link.label }}</router-link>
		</div>
	</div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import { Prop } from "vue-property-decorator";

export default class NavBar extends Vue {
	@Prop({ default: [] }) links!: { href: string, label: string }[];
	@Prop({ default: "No Logo" }) logo!: string;
}
</script>

<style lang="less" scoped>
@import "./Config";

.root {
	width: 100%;
	height: 40px;
	background: @layer0;
	box-shadow: 0 -1px 0px 1px @dynamic1;
	display: flex;
	align-items: center;
	justify-content: space-between;
	padding: 0 10px;
	flex-direction: row;

	.logo {
		color: @accent;
		font-family: @mainFont;
		font-size: 13px;
		margin-left: -5px;
		text-decoration: none;
		transition: 100ms;
		padding: 5px;

		&:after {
			content: "";
			display: flex;
			width: 100%;
			border-radius: 3px;
			height: 1px;
			transition: 100ms;
		}

		&:hover {
			color: @textDim;

			&:after {
				background: @accent;
			}
		}
	}

	.links {
		margin-right: -10px;
		display: flex;

		a {
			margin-right: 10px;
			color: @textDim;
			text-decoration: none;
			transition: 100ms;
			font-family: @mainFont;
			font-size: 13px;
			height: 30px;
			border-radius: 3px;
			display: flex;
			padding: 5px;
			cursor: default;
			align-items: center;

			&:hover {
				color: @text;
			}

			&.router-link-active {
				color: @accent;
			}
		}
	}
}
</style>