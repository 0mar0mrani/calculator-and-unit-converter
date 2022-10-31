<template>
	<section>
		<div class="calculator__display">{{ display }}</div>

		<button @click="displayNumberOperator($event)">1</button>
		<button @click="displayNumberOperator($event)">2</button>
		<button @click="displayNumberOperator($event)">3</button>
		<button @click="displayNumberOperator($event)">4</button>
		<button @click="displayNumberOperator($event)">5</button>
		<button @click="displayNumberOperator($event)">6</button>
		<button @click="displayNumberOperator($event)">7</button>
		<button @click="displayNumberOperator($event)">8</button>
		<button @click="displayNumberOperator($event)">9</button>
		<button @click="displayNumberOperator($event)">0</button>

		<button @click="displayNumberOperator($event)">.</button>

		<button @click="displayNumberOperator($event)">+</button>
		<button @click="displayNumberOperator($event)">-</button>
		<button @click="displayNumberOperator($event)">*</button>
		<button @click="displayNumberOperator($event)">/</button>

		<button @click="resetCalculator">C</button>
		
		<button @click="calculateEquation">=</button>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				display: '',
			}
		},

		methods: {
			calculateEquation() {
				const answer = eval(this.display);
				this.display = answer;
				console.log(answer);
			},

			displayNumberOperator(event) {
				const buttonValue = event.target.innerText;
				this.display += buttonValue;
				console.log(this.display);
			},
			}
		}
	}
</script>

<style></style>