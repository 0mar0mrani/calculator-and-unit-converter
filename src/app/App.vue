<template>
	<Calculator/>
	<UnitConverterContainer/>
</template>

<script>
	import Calculator from '../components/Calculator.vue'
	import LengthConverter from '../components/LengthConverter.vue'
	import WeightConverter from '../components/WeightConverter.vue'
	import UnitConverterContainer from '../components/UnitConverterContainer.vue'

	export default {
		components: {
			Calculator,
			LengthConverter,
			WeightConverter,
			UnitConverterContainer,
		},
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