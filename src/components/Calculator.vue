<template>
	<section>
		<button @click="calculate">=</button>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				values: ['78', '+', '5', '*','6']
			}
		},

		methods: {
			calculate() {
				const calculationString = this.values.reduce((totalValue, oneInput) => totalValue + oneInput);
				const answer = eval(calculationString);
				console.log(answer);
				return answer;
			}
		}
	}
</script>

<style></style>