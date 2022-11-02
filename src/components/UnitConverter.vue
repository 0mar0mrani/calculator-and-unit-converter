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
