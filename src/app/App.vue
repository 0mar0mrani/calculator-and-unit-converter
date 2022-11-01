<template>
	<Calculator/>
</template>

<script>
	import Calculator from '../components/Calculator.vue'

	export default {
		components: {
			Calculator,
		}
	}
</script>

<style>
	* {
		box-sizing: border-box;
		padding: 0;
		margin: 0;
	}

	html {
		font-size: 10px;
	}

	body {
		font-family: 'futura-pt', sans-serif;
		background-color: #FAF3DD;
	}
</style>