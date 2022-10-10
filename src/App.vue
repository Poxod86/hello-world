<template>
	<div class="calc">
		<div class="display">
			<input v-model.number="operand1" type="text"/>
			<p> + </p>
			<input v-model.number="operand2" type="text"/>
			= 
			<input v-model="result" type="text" readonly/>
		</div>
		<div v-if="error" class="error"> {{ error }} </div>
		<div class="keyboards">
			<div class="row">
				<button v-for="item in operators" v-bind:key ="item" @click ="getResult(item)">{{ item }}</button>
				
			</div>
		</div>
	</div>
		
	
</template>

<script>

export default {
  name: 'App',
  	data() {
			return {
			operand1: 0,
			operand2: 0,
			numbers: [1,2,3,4,5,6,7,8,9,0],
			operators: ['+','-','*','/','**'],
			result: 0,
			error: ''
		}
	},
	methods: {
		getResult(operator){
			this.error ='';
			switch (operator) {
				case "+":
					this.result = this.operand1 + this.operand2
					break;
				case "-":
					this.result = this.operand1 - this.operand2
					break;
				case "*":
					this.result = this.operand1 * this.operand2
					break;
				case "/":
					if(this.operand2 == 0) {
						this.error = 'На ноль делить нельзя !'
					} else {
						this.result = this.operand1 / this.operand2
					}
					
					break;
				case "**":
					this.result = this.operand1 ** this.operand2
					break;
				case "//":
					this.result = Math.floor(this.operand1 + this.operand2)
					break;
			
				default:
					break;
			}
		}
		
	}
}
</script>

<style>
	* {
		font-family: 'Gilroy',sans-serif;
		transition: 0.3s all;
		font-weight: 600;
	}
	.calc {
		max-width: 600px;
		margin: 0 auto;
	}
	.display {
		display: flex;
		flex-direction: row;
		align-items: center;
		width: 600px;
		
		margin: 50px auto;
	}
	input[type="text"] {
		width: 190px;
		border: 0 solid gray;
		color: #243849;
		font-size: 18px;
		padding: 5px 5px;
		text-align: right;
		box-shadow: 0 3px 15px grey;
	}
	.keyboards{
		margin: 0 auto;
		text-align: center;
	}
</style>
