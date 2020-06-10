<template>
	<div class="ask">
		<article>{{ message }}</article>
		<div class="bottom">
			<button @click="getShow">对！</button>
			<button @click="getShow">没错！</button>
		</div>
	</div>
</template>
<script>
export default {
	props: {
		message: "",
	},
	methods: {
		getShow() {
			this.$emit("getShow", false);
		},
	},
};
</script>
<style lang="scss" scoped>
.ask {
	width: calc(100% - 100px);
	margin-left: -50px;
	position: absolute;
	top: 0;
	border: 1px solid black;
	background-color: #fff;
	padding: 50px;
}
</style>
