<template>
	<Calculator/>

	<div class="container">
		<div class="buttons">
			<button class="button button-left " :class="{ buttonLengthActive : showLength }" @click="showLengthConverter">
				<img src="../../assets/svg/length.svg" alt="Weight icon">
			</button>
			
			<button class="button button-right " :class="{ buttonWeightActive : showWeight }" @click="showWeightConverter">
				<img src="../../assets/svg/weight.svg" alt="Weight icon">
			</button>
		</div>
			
		<LengthConverter v-if="showLength === true"/>
		<WeightConverter v-if="showWeight === true"/>
	</div>
</template>

<script>
	import Calculator from '../components/Calculator.vue'
	import LengthConverter from '../components/LengthConverter.vue'
	import WeightConverter from '../components/WeightConverter.vue'

	export default {
		components: {
			Calculator,
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
	* {
		box-sizing: border-box;
		padding: 0;
		margin: 0;
	}

	html {
		font-size: 10px;
	}

	body {
		font-family: 'futura-pt', sans-serif;
		background-color: #FAF3DD;
	}

	.container {
		display: flex;
		flex-direction: column;
		max-width: 40rem;
		margin: 0 auto;
		box-shadow: 0.3rem 0.3rem #000;
		border-radius: 1rem;
		margin-bottom: 10rem;
	}

	.buttons {
		display: flex;
	}

	.button {
		background-color: #696969;
		height: 6rem;
		width: 50%;
		border: none;
		cursor: pointer;
		transition: all 0.1s;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.button img {
		width: 4rem;
		height: 4rem;
		transition: all 0.3s;
		transform: scale(0.8);
	}

	.button-left {
		border-left: solid 2px #000;
		border-top: solid 2px #000;
		border-right: solid 2px #000;
		border-bottom: solid 2px #000;
		z-index: 1;
		border-radius: 1rem 0 0 0;
	}

	.button-right {
		border-right: solid 2px #000;
		border-top: solid 2px #000;
		border-bottom: solid 2px #000;
		border-radius: 0 1rem 0 0;
	}

	/* .button:hover  img {
		transform: scale(0.8);
	} */

	.buttonLengthActive {
		background-color: #F2D7EE;
		border-bottom: unset;
		cursor: unset;
	} 
	
	.buttonWeightActive {
		background-color: #D9F7FA;
		border-bottom: unset;
		cursor: unset;
	}
	
	.buttonLengthActive img,
	.buttonWeightActive img {
		transform: scale(1);
	}

</style>