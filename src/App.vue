<template>
	<div class="calc">
		<div class="display">
			<input v-model.number="operand1" type="text"/>
			<p> {{ operator }} </p>
			<input v-model.number="operand2" type="text"/>
			= 
			<input v-model="result" type="text" readonly/>
		</div>
		<div v-if="error" class="error"> {{ error }} </div>
		<div class="keyboards">
			<div class="row">
				<button v-for="item in operators" :key ="item" @click ="setOperator(item)">{{ item }}</button>
				
			</div>
		</div>
		<input type="checkbox" v-model="light" v-bind:true-value="on" v-bind:false-value="off" />
      <span v-if="light===on">Убрать экранную клавиатуру <br>
				<button v-for="item in numbers" :key ="item" @click ="setOperand(item)">{{ item }}</button>
				<button @click ="reset">Reset</button>
			
      
		<br>
			<input type="radio" value="operand1" v-model="operand">
			<label>Операнд-1</label>
			<input type="radio" value="operand2" v-model="operand">
			<label>Операнд-2</label>
		</span><span v-else>Отобразить экранную клавиатуру</span>	

	
	</div>
		
	
</template>

<script>


export default {
  name: 'App',
  	data() {
			return {
			operand: "",
			operand1: "",
			operand2: "",
			operator: '+',
			numbers: [1,2,3,4,5,6,7,8,9,0],
			operators: ['+','-','*','/','**'],
			error: '',
			on: true,
      off:false,
      light: false
		}
	},

	computed:{
		result() {
			this.error ='';
			switch (this.operator) {
				case "+":
					return  this.operand1 + this.operand2
					break;
				case "-":
				return this.operand1 - this.operand2
					break;
				case "*":
				return this.operand1 * this.operand2
					break;
				case "/":
					if(this.operand2 == 0) {
						return 'На ноль делить нельзя !'
					} else {
						return this.operand1 / this.operand2
					}
					
					break;
				case "**":
				return this.operand1 ** this.operand2
					break;
				case "//":
				return Math.floor(this.operand1 + this.operand2)
					break;
			
				default:
					break;
			}
		}
	},

	methods: {
		setOperator(operator) {
			this.operator = operator
		},
		setOperand(operand2) {
			  
				this.operand2 = Number(String(this.operand2)+ String(operand2))
			
		},
		reset() {
			this.operator = "+",
			this.operand1 = "",
			this.operand2 = "",
			this.result =""
		},
		
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
