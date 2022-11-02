<template>
	<section class="unitConverter">
		<label class="unitConverter__header" for="length">Length</label>
		<legend class="unitConverter__section1">
			<input @input="valueToMillimeter" class="unitConverter__input1" type="number" v-model="meter">
	
			<select class="unitConverter__selector1">
				<option value="meter">Meter</option>
				<option value="millimeter">Millimeter</option>
				<option value="centimeter">Centimeter</option>
				<option value="decimeter">Decimeter</option>
			</select>
		</legend>

		<legend class="unitConverter__section2">	
			<input @input="valueToMeter" class="unitConverter__input2" type="number" v-model="millimeter">
	
			<select class="unitConverter__selector2">
				<option value="millimeter">Millimeter</option>
				<option value="centimeter">Centimeter</option>
				<option value="decimeter">Decimeter</option>
				<option value="meter">Meter</option>
			</select>
		</legend>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				meter: '',
				millimeter: '',
			}
		},

		computed: {
		},

		methods: {
			valueToMeter() {
				this.meter = '';
				const meter = this.millimeter / 1000;

				if (meter !== 0) {
					return this.meter = meter;
				}
			},

			valueToMillimeter() {
				this.millimeter = '';
				const millimeter = this.meter * 1000;

				if (millimeter !== 0) {
					return this.millimeter = millimeter;
				}
			}

		}
	}
</script>

<style>
	.unitConverter {
		max-width: 40rem;
		margin: 10rem auto;
		display: flex;
		flex-direction: column;
	}

	.unitConverter__section1,
	.unitConverter__section2 {
		display: flex;
	}

	.unitConverter__input1, 
	.unitConverter__input2 {
		flex-grow: 1;
		font-size: 3rem;
	}

	.unitConverter__header {
		font-size: 4rem;
		font-weight: 600;
	}

	.unitConverter__selector1,
	.unitConverter__selector2 {
		font-size: 2rem;
		font-weight: 600;
	}
</style>