<template>
	<div class="ct-divider">
		{{divider}}
	</div>
</template>

<style scoped>
	.ct-divider {
		display: flex;
		align-items: flex-start;
		margin: 10px;
		font-size: 6vw;
	}
</style>

<script>
	export default {
		props: {
			divider: {
				type: String,
				default: ":"
			}
		}
	};
</script>
