<template>
	<section class="unitConverter">
		<label class="unitConverter__header" for="length">Length</label>
		<legend class="unitConverter__section1">
			<input @input="displayToSection2" class="unitConverter__input1" type="number" v-model="section1.display">

			<select @change="displayToSection1"  v-model="section1.unit"  class="unitConverter__selector1">
				<option value="millimeter">Millimeter</option>
				<option value="centimeter">Centimeter</option>
				<option value="decimeter">Decimeter</option>
				<option value="meter">Meter</option>
				<option value="foot">Foot</option>
			</select>
		</legend>

		<legend class="unitConverter__section2">	
			<input @input="displayToSection1" class="unitConverter__input2" type="number" v-model="section2.display">
	
			<select @change="displayToSection2" v-model="section2.unit" class="unitConverter__selector2">
				<option value="millimeter">Millimeter</option>
				<option value="centimeter">Centimeter</option>
				<option value="decimeter">Decimeter</option>
				<option value="meter">Meter</option>
				<option value="foot">Foot</option>
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
					unit: "millimeter",
				},
				
				section2: {
					display: '',
					unit: "millimeter",
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
					case 'millimeter': 
						return object.display;

					case 'centimeter':
						return object.display * 10;

					case 'decimeter':
						return object.display * 100;
					
					case 'meter':
						return object.display * 1000;

					case 'foot':
						return object.display * 304.8;
				}
			},

			convertMillimetersToRightUnit(object, computed) {
				switch(object.unit) {
					case 'millimeter':
						return computed;

					case 'centimeter':
						return computed / 10;

					case 'decimeter':
						return computed / 100;
					
					case 'meter':
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

<style>
	.unitConverter {
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

	.unitConverter--blue {
		background-color: #D9F7FA;
	}

	.unitConverter__header {
		font-size: 4rem;
		font-weight: 600;
		margin-bottom: 2rem;
	}

	.unitConverter__section1,
	.unitConverter__section2 {
		display: flex;
		gap: 1rem;
		margin-bottom: 1rem;
	}

	.unitConverter__input1, 
	.unitConverter__input2 {
		flex-grow: 1;
		font-size: 3rem;
		width: 60%;
		border-radius: 0.5rem;
		border: solid 2px #000;
	}

	.unitConverter__selector1,
	.unitConverter__selector2 {
		font-size: 2rem;
		flex-grow: 1;
		font-weight: 600;
		width: 40%;
		border-radius: 0.5rem;
		border: solid 2px #000;
	}
</style>