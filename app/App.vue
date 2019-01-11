<template>
	<div id="app">
		<clockey></clockey>
	</div>
</template>

<style>
	body, html {
		padding: 0;
		margin: 0;
	}
</style>

<style scoped>
	#app {
		max-width: 100vw;
		overflow-x: hidden;

		min-height: 100vh;
		background: #1396f2;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	* {
		color: #fff;
		font-family: "Roboto", sans-serif;
		font-weight: 100;
	}
</style>

<script>
	import Clockey from "./components/Clockey.vue";

	export default {
		components: {
			Clockey
		}
	};
</script>
