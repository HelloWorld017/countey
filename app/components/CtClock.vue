<template>
	<div class="ct-clock">
		<template v-if="animate">
			<div class="numbers">
				<ct-number v-for="count in (counts)" :number="numbers[count - 1]"></ct-number>
			</div>
		</template>
		<span class="left" v-else>
			{{left}}
		</span>

		<span class="clock-unit">
			{{unitName}}
		</span>
	</div>
</template>

<style scoped>
	.ct-clock {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin: 1vw;
	}

	.left {
		font-size: 6vw;
	}

	.numbers {
		display: flex;
	}

	.clock-unit {
		font-weight: 400;
		font-size: 1vw;
	}
</style>

<script>
	import CtNumber from "./CtNumber.vue";

	export default {
		props: {
			unit: {
				type: Number,
				default: 1000
			},

			unitName: {
				type: String,
				default: "Seconds"
			},

			unitBase: {
				type: Number,
				default: Infinity
			},

			target: {
				type: Number,
				default: Date.now()
			},

			current: {
				type: Number,
				default: Date.now()
			},

			animate: {
				type: Boolean
			},
			
			counts: {
				type: Number,
				default: 2
			}
		},

		methods: {
			padn(n, i) {
				return i.toString().padStart(n, '0');
			},

			floorToZero(i) {
				return i > 0 ? Math.floor(i) : Math.ceil(i);
			}
		},

		computed: {
			left() {
				return this.padn(this.counts, Math.abs(this.floorToZero((this.target - this.current) / this.unit) % this.unitBase));
			},

			numbers() {
				return this.left.split('');
			}
		},

		components: {
			CtNumber
		}
	};
</script>
