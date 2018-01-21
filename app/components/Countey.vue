<template>
	<section class="countey">
		<ct-divider class="minus" divider="-" v-if="isMinus"></ct-divider>
		<ct-clock :unit="604800000" unit-name="Weeks" :target="target" :current="current" animate />
		<ct-divider></ct-divider>
		<ct-clock :unit="86400000" unit-name="Days" :unit-base="7" :target="target" :current="current" animate />
		<ct-divider></ct-divider>
		<ct-clock :unit="3600000" unit-name="Hours" :unit-base="24" :target="target" :current="current" animate />
		<ct-divider></ct-divider>
		<ct-clock :unit="60000" unit-name="Minutes" :unit-base="60" :target="target" :current="current" animate />
		<ct-divider></ct-divider>
		<ct-clock :unit="1000" unit-name="Seconds" :unit-base="60" :target="target" :current="current" animate />
		<ct-divider divider="."></ct-divider>
		<ct-clock :unit="10" unit-name="Centiseconds" :unit-base="100" :target="target" :current="current" />
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
	import CtClock from "./CtClock.vue";
	import CtDivider from "./CtDivider.vue";

	export default {
		data() {
			return {
				current: Date.now(),
				intervalId: undefined
			};
		},

		computed: {
			isMinus() {
				return this.target - this.current < 0;
			}
		},

		props: {
			target: {
				type: Number,
				default: new Date("2018.11.15 00:00 GMT+09").getTime()
			}
		},

		mounted() {
			this.intervalId = setInterval(() => {
				this.current = Date.now();
			}, 10);
		},

		destroyed() {
			clearInterval(this.intervalId);
		},

		components: {
			CtClock,
			CtDivider
		}
	};
</script>
