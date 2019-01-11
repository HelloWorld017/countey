<template>
	<section class="countey">
		<ck-clock unit-name="Date" :current="current.getDate()" animate />
		<ct-divider divider="/"></ct-divider>
		<ck-clock unit-name="Hours" :current="current.getHours()" animate />
		<ct-divider></ct-divider>
		<ck-clock unit-name="Minutes" :current="current.getMinutes()" animate />
		<ct-divider></ct-divider>
		<ck-clock unit-name="Seconds" :current="current.getSeconds()" animate />
	</section>
</template>

<style scoped>
	.countey {
		display: flex;
	}

	@media screen and (max-width: 768px) {
		.countey {
			flex-direction: column;
		}

		.ct-clock {
			margin-top: 1vh;
		}

		.ct-divider:not(.minus) {
			display: none;
		}
	}
</style>

<script>
	import CkClock from "./CkClock.vue";
	import CtDivider from "./CtDivider.vue";

	export default {
		data() {
			return {
				current: new Date(),
				intervalId: undefined
			};
		},

		computed: {
			isMinus() {
				return this.target - this.current < 0;
			}
		},

		mounted() {
			this.intervalId = setInterval(() => {
				this.current = new Date();
			}, 50);
		},
		
		destroyed() {
			clearInterval(this.intervalId);
		},

		components: {
			CkClock,
			CtDivider
		}
	};
</script>
