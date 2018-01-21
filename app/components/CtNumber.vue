<template>
	<div class="ct-number">
		<transition name="slide" mode="out-in">
			<div v-for="i in numTexts" v-if="i === number" :key="i">
				{{i}}
			</div>
		</transition>
	</div>
</template>

<style scoped>
	.ct-number {
		display: flex;
		font-size: 6vw;
		overflow-x: hidden;
		overflow-y: hidden;
		padding-left: 3vw;
		padding-right: 12vw;
		margin-left: -3vw;
		margin-right: -12vw;
	}

	.slide-enter-active, .slide-leave-active {
		transition: all .4s ease;
	}

	.slide-enter {
		transform: translateX(-6vw);
	}

	.slide-leave-to {
		transform: skewX(40deg) translateY(6vw);
	}
</style>

<script>
	export default {
		data() {
			return {
				numTexts: [...Array(10)].map((v, i) => `${i}`)
			};
		},

		props: ['number']
	};
</script>
