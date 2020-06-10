<template>
	<div id="app">
		<div class="title">
			<button id="button" @click="take(`你根本就不想出校门`)">
				你想出校门吗?
			</button>
		</div>
		<div class="choose">
			<button
				id="button"
				type="warning"
				@click="take(`你是个爱学习的好青年`)"
				@mouseenter="changeWord(1)"
				@mouseleave="changeWord(3)"
			>
				{{ want1 }}
			</button>
			<button id="button" @click="take(`你是个爱学习的好青年`)" type="warning">
				{{ want2 }}
			</button>
		</div>
		<div class="bottom">
			<button
				id="button"
				type="danger"
				@mouseenter="changeLeave(0)"
				@mouseleave="changeLeave(1)"
				@click="take(`行行行~我知道了`)"
			>
				{{ leave }}
			</button>
			<button id="button" type="danger" ref="author" @mouseenter="about">
				联系作者
			</button>
		</div>
		<ask :message="mess" v-show="show" @getShow="showShow"></ask>
	</div>
</template>

<script>
import ask from "./ask.vue";
export default {
	name: "App",
	components: {
		ask,
	},
	data() {
		return {
			want1: "想",
			want2: "不想",
			leave: "作者你不想出校门?",
			mess: "123",
			show: false,
		};
	},
	methods: {
		/**
		 * 改变按钮
		 */
		changeWord(index) {
			if (index == 1) {
				this.want1 = "不想";
				this.want2 = "想";
			} else if (index == 2 || index == 3) {
				this.want1 = "想";
				this.want2 = "不想";
			}
		},
		/**
		 * 出校门
		 */
		changeLeave(index) {
			if (index == 0) {
				this.leave = "我就是不想出校门！";
			} else {
				this.leave = "作者你不想出校门吗？";
			}
		},
		/**
		 * 联系作者
		 */
		about() {
			let author = this.$refs.author;
			const num1 = Math.floor(Math.random() * 100);
			const num2 = Math.floor(Math.random() * 100);
			author.setAttribute(
				"style",
				"position: absolute;" + `top: ${num1}%;` + `left: ${num2}%`
			);
		},
		showShow(val) {
			this.show = val;
		},
		take(str) {
			this.mess = str;
			this.show = true;
		},
	},
};
</script>

<style lang="scss">
#app {
	position: absolute;
	left: 0;
	top: 0;
	width: 40%;
	border: 1px solid black;
	padding: 50px;
	margin-left: calc(30% - 50px);
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
	.choose,
	.bottom {
		display: flex;
		justify-content: space-around;
		align-items: center;
		width: 100%;
		padding: 6% 0;
	}
	.bottom {
		justify-content: space-between;
	}
}
#button {
	width: 12rem;
	font-weight: bold;
	font-size: 0.9rem;
	letter-spacing: 2px;
}
</style>
