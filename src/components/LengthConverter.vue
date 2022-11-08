<template>
	<section class="unit-converter">
		<label class="unit-converter__header" for="length">Length</label>
		<legend class="unit-converter__section1">
			<input @input="handleConverter1Input" class="unit-converter__input1" type="number" v-model="section1.input">

			<select @change="handleConverter1Change"  v-model="section1.unit"  class="unit-converter__selector1">
				<option value="millimeter">Millimeters</option>
				<option value="centimeter">Centimeters</option>
				<option value="decimeter">Decimeters</option>
				<option value="meter">Meters</option>
				<option value="foot">Feet</option>
			</select>
		</legend>

		<legend class="unit-converter__section2">	
			<input @input="handleConverter2Input" class="unit-converter__input2" type="number" v-model="section2.input">
	
			<select @change="handleConverter2Change" v-model="section2.unit" class="unit-converter__selector2">
				<option value="millimeter">Millimeters</option>
				<option value="centimeter">Centimeters</option>
				<option value="decimeter">Decimeters</option>
				<option value="meter">Meters</option>
				<option value="foot">Feet</option>
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
					unit: "foot",
				},
				
				section2: {
					input: '',
					unit: "meter",
				},
			}
		},

		computed: {
			section1ValueInMillimeters() {
				return this.convertValueToMillimeters(this.section1);
			},

			section2ValueInMillimeters() {
				return this.convertValueToMillimeters(this.section2);
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
			convertValueToMillimeters(object) {
				switch(object.unit) {
					case 'millimeter': 
						return object.input;

					case 'centimeter':
						return object.input * 10;

					case 'decimeter':
						return object.input * 100;
					
					case 'meter':
						return object.input * 1000;

					case 'foot':
						return object.input * 304.8;
				}
			},

			convertMillimetersToRightUnit(object, computedNumber) {
				switch(object.unit) {
					case 'millimeter':
						return computedNumber;

					case 'centimeter':
						return computedNumber / 10;

					case 'decimeter':
						return computedNumber / 100;
					
					case 'meter':
						return computedNumber / 1000;
					
					case 'foot':
						return computedNumber / 304.8;
				}
			},

			calculateAndDisplayResultToSection1() {
				this.section1.input = '';
				const value = this.convertMillimetersToRightUnit(this.section1, this.section2ValueInMillimeters);

				if (value !== 0) {
					this.section1.input = value;
				}
			},

			calculateAndDisplayResultToSection2() {
				this.section2.input = '';
				const value = this.convertMillimetersToRightUnit(this.section2, this.section1ValueInMillimeters);
				
				if (value !== 0) {
					this.section2.input = value;
				}
			},
		}
	}
</script>

<style scoped>
	.unit-converter {
		max-width: 40rem;
		margin: 0 auto;
		display: flex;
		flex-direction: column;
		background-color: #F2D7EE;
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
			padding-bottom: 2rem;
			margin-bottom: 0;
			border-bottom: solid 1px #000;
		}

		.unit-converter__section2 {
			padding-top: 2rem;
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