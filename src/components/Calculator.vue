<template>
	<section class="calculator">
		<div class="calculator__display">
			{{ display }}
		</div>

		<div class="calculator__buttons">
			<button @click="handleOperatorInput('+')" class="calculator__operator">+</button>
			<button @click="handleOperatorInput('-')" class="calculator__operator">-</button>
			<button @click="handleOperatorInput('×')" class="calculator__operator">×</button>
			<button @click="handleOperatorInput('÷')" class="calculator__operator">÷</button>

			<button @click="handleNumberInput('7')" class="calculator__number">7</button>
			<button @click="handleNumberInput('8')" class="calculator__number">8</button>
			<button @click="handleNumberInput('9')" class="calculator__number">9</button>

			<button @click="handleNumberInput('4')" class="calculator__number">4</button>
			<button @click="handleNumberInput('5')" class="calculator__number">5</button>
			<button @click="handleNumberInput('6')" class="calculator__number">6</button>


			<button @click="handleNumberInput('1')" class="calculator__number">1</button>
			<button @click="handleNumberInput('2')" class="calculator__number">2</button>
			<button @click="handleNumberInput('3')" class="calculator__number">3</button>
	

			<button @click="handleNumberInput('.')" class="calculator__period">.</button>
			<button @click="handleNumberInput('0')" class="calculator__number">0</button>
			<button @click="clearResult" class="calculator__reset">C</button>

			<button @click="handleEqualsInput" class="calculator__equals">=</button>
		</div>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				display: '',
				currentNumber: '',
				calculationArray: [],
			}
		},

		computed: {
			currentNumberAsNumber() {
				return Number(this.currentNumber)
			},
		},

		methods: {
			clearResult() {
				this.display = '';
				this.currentNumber = '';
				this.calculationArray = [];
			},
			
			handleOperatorInput(operator) {
				this.display += operator;

				if (this.currentNumber !== '') {
					this.calculationArray.push(this.currentNumberAsNumber)
				} 
				
				this.calculationArray.push(operator)
				this.currentNumber = '';
			},

			handleNumberInput(number) {
				this.display += number;
				this.currentNumber += number;
			},
			
			handleEqualsInput() {
				this.calculationArray.push(this.currentNumberAsNumber)
				const answer = this.calculateArray();				
				this.calculationArray = [];

				if (isNaN(answer) === true) {
					this.display = 'ERROR';
				} else {
					this.display = answer;
					this.currentNumber = answer;
				}
			},

			calculateArray() {
				let currentOperator = null;
				let indexOfCurrentOperator;

				const answer = this.calculationArray.reduce((previousValue, currentValue, index) => {
					if (typeof currentValue === 'number') {
						
						if (currentOperator !== null) {
							switch(currentOperator) {
								case '+':
									return previousValue + currentValue;
								case '-':
									return previousValue - currentValue;
								case '÷':
									return previousValue / currentValue;
								case '×':
									return previousValue * currentValue;
							} 

						} else {
							return currentValue;
						}

					} else if (typeof currentValue === 'string') {
						if (index - 1 === indexOfCurrentOperator) {
							return NaN;

						} else {
							currentOperator = currentValue;
							indexOfCurrentOperator = index;
							return previousValue;
						}
					}

				}, 0);

				return answer;
			},
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
		background-color: #7B8CDE;
	}

	.calculator__display {
		width: 100%;
		height: 10rem;
		font-size: 6rem;
		line-height: 10rem;
		margin-bottom: 2rem;
		border: solid 2px #000;
		border-radius: 2rem;
		background-color: #fff;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
	}

	.calculator__buttons {
		display: grid;
		gap: 1rem;
		grid-template-columns: repeat(4, 1fr);
	}

	.calculator__number,
	.calculator__period,
	.calculator__operator,
	.calculator__reset,
	.calculator__equals {
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 4rem;
		width: 80%;
		aspect-ratio : 1 / 1;
		border-radius: 100%;
		border: solid 2px #000;
		box-shadow: 0.5rem 0.5rem #000;
		cursor: pointer;
		transition: all 0.2s;
		margin: 0 auto;
		background-color: #fff;
	}

	.calculator__number:active,
	.calculator__period:active,
	.calculator__operator:active,
	.calculator__reset:active,
	.calculator__equals:active {
		box-shadow: 0rem 0rem #000;
		transform: translate(0.5rem, 0.5rem);
	}

	.calculator__equals {
		aspect-ratio: unset;
		grid-column: 4 / 5;
		grid-row: 2 / 6;
		border-radius: 2rem;
		width: 100%;
	}

	@media screen and (max-width: 430px) {
		.calculator {
			margin: 10rem 2rem;
		}
	}

	@media screen and (max-width: 350px) {
	.calculator {
		margin: 10rem 1rem;
	}

	.calculator__number,
	.calculator__period,
	.calculator__operator,
	.calculator__reset,
	.calculator__equals {
		font-size: 2.5rem;
	}

	.calculator__display {
		font-size: 5rem;
	}
}
</style>