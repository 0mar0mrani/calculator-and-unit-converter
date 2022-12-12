<template>
	<section class="unit-converter">
		<label class="unit-converter__header" for="length">Weight</label>
		<legend class="unit-converter__section1">
			<input @input="handleConverter1Input" class="unit-converter__input1" type="number" v-model="section1.input">

			<select @change="handleConverter1Change"  v-model="section1.unit"  class="unit-converter__selector1">
				<option value="gram">Grams</option>
				<option value="decogram">Decograms</option>
				<option value="hectogram">Hectograms</option>
				<option value="kilogramgram">Kilograms</option>
				<option value="ounce">Ounces</option>
				<option value="pound">Punds</option>
			</select>
		</legend>

		<legend class="unit-converter__section2">	
			<input @input="handleConverter2Input" class="unit-converter__input2" type="number" v-model="section2.input">
	
			<select @change="handleConverter2Change" v-model="section2.unit" class="unit-converter__selector2">
				<option value="gram">Grams</option>
				<option value="decogram">Decograms</option>
				<option value="hectogram">Hectograms</option>
				<option value="kilogramgram">Kilograms</option>
				<option value="ounce">Ounces</option>
				<option value="pound">Punds</option>
			</select>
		</legend>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				section1: {
					input: '',
					unit: "pound",
				},
				
				section2: {
					input: '',
					unit: "kilogramgram",
				},
			}
		},

		computed: {
			section1ValueInGram() {
				return this.convertValueToGram(this.section1);
			},

			section2ValueInGram() {
				return this.convertValueToGram(this.section2);
			}
		},

		methods: {
			// Handler
			handleConverter1Input() {
				this.calculateAndDisplayResultToSection2();
			},

			handleConverter1Change() {
				this.calculateAndDisplayResultToSection1();
			},

			handleConverter2Input() {
				this.calculateAndDisplayResultToSection1();
			},

			handleConverter2Change() {
				this.calculateAndDisplayResultToSection2();
			},
			
			// Methods
			convertValueToGram(object) {
				switch(object.unit) {
					case 'gram': 
						return object.input;

					case 'decogram':
						return object.input * 10;

					case 'hectogram':
						return object.input * 100;
					
					case 'kilogramgram':
						return object.input * 1000;

					case 'ounce':
						return object.input * 28.3495231;
					
					case 'pound':
						return object.input * 453.59237;
				}
			},

			convertGramToRightUnit(object, computed) {
				switch(object.unit) {
					case 'gram':
						return computed;

					case 'decogram':
						return computed / 10;

					case 'hectogram':
						return computed / 100;
					
					case 'kilogramgram':
						return computed / 1000;
					
					case 'ounce':
						return computed / 28.3495231;
					
					case 'pound':
						return computed / 453.59237;
				}
			},

			calculateAndDisplayResultToSection1() {
				this.section1.input = '';
				const value = this.convertGramToRightUnit(this.section1, this.section2ValueInGram);

				if (value !== 0) {
					this.section1.input = value;
				}
			},

			calculateAndDisplayResultToSection2() {
				this.section2.input = '';
				const value = this.convertGramToRightUnit(this.section2, this.section1ValueInGram);
				
				if (value !== 0) {
					this.section2.input = value;
				}
			},
		}
	}
</script>

<style scoped>
	.unit-converter {
		display: flex;
		flex-direction: column;
		max-width: 40rem;
		margin: 0 auto;
		background-color: #D9F7FA;
		padding: 2rem;
		border-left: solid 2px #000;
		border-right: solid 2px #000;
		border-bottom: solid 2px #000;
		border-radius:  0 0 1rem 1rem;
	}

	.unit-converter__header {
		font-size: 4rem;
		font-weight: 600;
		margin-bottom: 2rem;
	}

	.unit-converter__section1,
	.unit-converter__section2 {
		display: flex;
		gap: 1rem;
		margin-bottom: 1rem;
	}

	.unit-converter__input1, 
	.unit-converter__input2 {
		flex-grow: 1;
		font-size: 3.5rem;
		width: 60%;
		border-radius: 0.5rem;
		border: solid 2px #000;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
	}

	.unit-converter__selector1,
	.unit-converter__selector2 {
		font-size: 2rem;
		flex-grow: 1;
		font-weight: 600;
		width: 40%;
		border-radius: 0.5rem;
		border: solid 2px #000;
	}

	@media screen and (max-width: 350px) {
		.unit-converter__section1 {
			margin-bottom: 4rem;
		}
		.unit-converter__section1,
		.unit-converter__section2 {
			display: flex;
			flex-direction: column;
		}

		.unit-converter__selector1,
		.unit-converter__selector2 {
			order: 1;
			width: 100%;
		}

		.unit-converter__input1, 
		.unit-converter__input2 {
			order: 2;
			flex-grow: 1;
			width: 100%;
		}
	}
</style>