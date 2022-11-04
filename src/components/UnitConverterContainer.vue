<template>
	<div class="unit-container">
		<div class="unit-container__buttons">
			<button class="unit-container__button unit-container__button--left " :class="{ 'unit-container__button--length' : showLength }" @click="showLengthConverter">
				<img src="../../assets/svg/length.svg" alt="Weight icon">
			</button>
			
			<button class="unit-container__button unit-container__button--right " :class="{ 'unit-container__button--weight' : showWeight }" @click="showWeightConverter">
				<img src="../../assets/svg/weight.svg" alt="Weight icon">
			</button>
		</div>
			
		<LengthConverter v-if="showLength === true"/>
		<WeightConverter v-if="showWeight === true"/>
	</div>
</template>


<script>
	import LengthConverter from '../components/LengthConverter.vue'
	import WeightConverter from '../components/WeightConverter.vue'

	export default {
		components: {
			LengthConverter,
			WeightConverter,
		},

		data() {
			return {
				showLength: true,
				showWeight: false,
			}
		},
		
		methods: {
			showLengthConverter() {
				this.showLength = true;
				this.showWeight = false;
			},
			
			showWeightConverter() {
				this.showLength = false;
				this.showWeight = true;
			}
		}
	}
</script>


<style>
	.unit-container {
		display: flex;
		flex-direction: column;
		max-width: 40rem;
		margin: 0 auto;
		box-shadow: 0.3rem 0.3rem #000;
		border-radius: 1rem;
		margin-bottom: 10rem;
	}

	.unit-container__buttons {
		display: flex;
	}

	.unit-container__button {
		background-color: #BEBEBE;
		height: 6rem;
		width: 50%;
		border: none;
		cursor: pointer;
		transition: all 0.1s;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.unit-container__button img {
		width: 4rem;
		height: 4rem;
		transition: all 0.3s;
		transform: scale(0.8);
	}

	.unit-container__button--left {
		border-left: solid 2px #000;
		border-top: solid 2px #000;
		border-right: solid 2px #000;
		border-bottom: solid 2px #000;
		z-index: 1;
		border-radius: 1rem 0 0 0;
	}

	.unit-container__button--right {
		border-right: solid 2px #000;
		border-top: solid 2px #000;
		border-bottom: solid 2px #000;
		border-radius: 0 1rem 0 0;
	}

	.unit-container__button--length {
		background-color: #F2D7EE;
		border-bottom: unset;
		cursor: unset;
	} 
	
	.unit-container__button--weight {
		background-color: #D9F7FA;
		border-bottom: unset;
		cursor: unset;
	}
	
	.unit-container__button--length img,
	.unit-container__button--weight img {
		transform: scale(1);
	}

	@media screen and (max-width: 430px) {
		.unit-container {
			margin: 0 2rem;
		}
	}

	@media screen and (max-width: 350px) {
		.unit-container {
			margin: 0 1rem;
		}
	}
</style>