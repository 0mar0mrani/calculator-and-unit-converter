<template>
	<section class="calculator">
		<div class="calculator__display">{{ display }}</div>

		<div class="calculator__buttons">
			<div class="calculator__numbers">
				<button @click="displayNumberOperator($event)" class="calculator__number">1</button>
				<button @click="displayNumberOperator($event)" class="calculator__number">2</button>
				<button @click="displayNumberOperator($event)" class="calculator__number">3</button>
				<button @click="displayNumberOperator($event)" class="calculator__number">4</button>
				<button @click="displayNumberOperator($event)" class="calculator__number">5</button>
				<button @click="displayNumberOperator($event)" class="calculator__number">6</button>
				<button @click="displayNumberOperator($event)" class="calculator__number">7</button>
				<button @click="displayNumberOperator($event)" class="calculator__number">8</button>
				<button @click="displayNumberOperator($event)" class="calculator__number">9</button>
				<button @click="displayNumberOperator($event)" class="calculator__number">0</button>
			</div>
				
			
			<div class="calculator__operators">
				<button @click="displayNumberOperator($event)" class="calculator__operator">+</button>
				<button @click="displayNumberOperator($event)" class="calculator__operator">-</button>
				<button @click="displayNumberOperator($event)" class="calculator__operator">*</button>
				<button @click="displayNumberOperator($event)" class="calculator__operator">/</button>
			</div>
			
			<button @click="displayNumberOperator($event)" class="calculator__period">.</button>
			<button @click="resetCalculator" class="calculator__reset">C</button>
			<button @click="calculateEquation" class="calculator__equals">=</button>
		</div>
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

			resetCalculator() {
				this.display = '';
				console.log(this.display);
			}
		}
	}
</script>

<style>
.calculator {
	display: flex;
	flex-direction: column;
}
.calculator__display {
	width: 100%;
	height: 6rem;
	font-size: 5rem;
	background-color: antiquewhite;
}

.calculator__number,
.calculator__period,
.calculator__operator,
.calculator__reset,
.calculator__equals {
	font-size: 2rem;
	width: 4rem;
	height: 4rem;
}
</style>