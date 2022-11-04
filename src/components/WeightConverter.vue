<template>
	<section class="unit-converter">
		<label class="unit-converter__header" for="length">Weight</label>
		<legend class="unit-converter__section1">
			<input @input="displayToSection2" class="unit-converter__input1" type="number" v-model="section1.display">

			<select @change="displayToSection1"  v-model="section1.unit"  class="unit-converter__selector1">
				<option value="gram">Gram</option>
				<option value="decogram">Decogram</option>
				<option value="hectogram">Hectogram</option>
				<option value="kilogramgram">Kilogram</option>
			</select>
		</legend>

		<legend class="unit-converter__section2">	
			<input @input="displayToSection1" class="unit-converter__input2" type="number" v-model="section2.display">
	
			<select @change="displayToSection2" v-model="section2.unit" class="unit-converter__selector2">
				<option value="gram">Gram</option>
				<option value="decogram">Decogram</option>
				<option value="hectogram">Hectogram</option>
				<option value="kilogramgram">Kilogram</option>
			</select>
		</legend>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				section1: {
					display: '',
					unit: "gram",
				},
				
				section2: {
					display: '',
					unit: "gram",
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
			convertValueToMillimeters(object) {
				switch(object.unit) {
					case 'gram': 
						return object.display;

					case 'decogram':
						return object.display * 10;

					case 'hectogram':
						return object.display * 100;
					
					case 'kilogramgram':
						return object.display * 1000;

					case 'foot':
						return object.display * 304.8;
				}
			},

			convertMillimetersToRightUnit(object, computed) {
				switch(object.unit) {
					case 'gram':
						return computed;

					case 'decogram':
						return computed / 10;

					case 'hectogram':
						return computed / 100;
					
					case 'kilogramgram':
						return computed / 1000;
					
					case 'foot':
						return computed / 304.8;
				}
			},

			displayToSection1() {
				this.section1.display = '';
				const value = this.convertMillimetersToRightUnit(this.section1, this.section2ValueInMillimeters);

				if (value !== 0) {
					this.section1.display = value;
				}
			},

			displayToSection2() {
				this.section2.display = '';
				const value = this.convertMillimetersToRightUnit(this.section2, this.section1ValueInMillimeters);
				
				if (value !== 0) {
					this.section2.display = value;
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
</style>