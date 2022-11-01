<template>
	<section class="calculator">
		<div class="calculator__display">{{ display }}</div>

		<div class="calculator__buttons">
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
			<button @click="displayNumberOperator($event)" class="calculator__operator">+</button>
			<button @click="displayNumberOperator($event)" class="calculator__operator">-</button>
			<button @click="displayNumberOperator($event)" class="calculator__operator">*</button>
			<button @click="displayNumberOperator($event)" class="calculator__operator">/</button>
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
			},

			displayNumberOperator(event) {
				const buttonValue = event.target.innerText;
				this.display += buttonValue;
			},

			resetCalculator() {
				this.display = '';
			}
		}
	}
</script>

<style>
	.calculator {
		max-width: 40rem;
		display: flex;
		margin: 10rem auto;
		flex-direction: column;
		border: solid 2px #000;
		padding: 2rem 1rem 2rem 1rem;
		border-radius: 1rem;
		box-shadow: 0.3rem 0.3rem #000;
	}

	.calculator__buttons {
		display: grid;
		gap: 1rem;
		grid-template-columns: repeat(4, 1fr);
	}

	.calculator__display {
		width: 100%;
		height: 10rem;
		font-size: 6rem;
		margin-bottom: 2rem;
		border: solid 2px #000;
		border-radius: 2rem;
	}

	.calculator__number,
	.calculator__period,
	.calculator__operator,
	.calculator__reset,
	.calculator__equals {
		font-size: 4rem;
		width: 80%;
		aspect-ratio : 1 / 1;
		border-radius: 100%;
		border: solid 2px #000;
		box-shadow: 0.5rem 0.5rem #000;
		cursor: pointer;
		transition: all 0.2s;
		margin: 0 auto;
	}

	.calculator__number:active,
	.calculator__period:active,
	.calculator__operator:active,
	.calculator__reset:active,
	.calculator__equals:active {
		box-shadow: 0rem 0rem #000;
		transform: translate(0.5rem, 0.5rem);
	}
</style>