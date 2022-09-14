<template>
  <div class="display">
		<div class="screen">
			<input @keyup.enter="calc()" type="text" v-model="result" placeholder="0">
		</div>
		<div class="keyboard">
			
      <div class="calc-num">
				<button @click="input(num)" class="cell num" v-for="num in numbers">{{num}}</button>
			</div>
      <button @click="input(op)" class="cell op" v-for="op in operators">{{op}}</button>
      <button @click="reset()" class="cell op">R</button>
      <button @click="calc()" class="cell op">=</button>
		</div>

	</div>
		
</template>

<script>

export default {
  name: 'App',
  	data() {
			return {
			numbers: [1,2,3,4,5,6,7,8,9,0],
			operators: ['+','-','*','/','**'],
			result: ''
		}
	},
	methods: {
		input: function(char) {
      this.result = this.result.toString();
      this.result+=char;
    },
		reset: function() {
      this.result = '';
    },
    calc: function() {
      this.result = eval(this.result);
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
	.display {
		width: 200px;
		box-shadow: 0 3px 15px grey;
	}
	input[type="text"] {
		width: 190px;
		border: 0;
		color: #243849;
		font-size: 18px;
		padding: 5px 5px;
		text-align: right;
	}
	.keyboard, .calc-num {
		display: flex;                       
		flex-wrap: wrap;  
		justify-content: space-around;
		width: 100%;
		
	}
	.cell {
		flex: 33%;                       
		height: 50px;
		font-size: 18px;
		border: none;
	}
	.num {
		background-color: #243849;
		color: #fff;
		font-weight: 400;
	}
	.cell:hover{
		background-color: #182530;
	}
	.op {
		background-color: #3cff00;
		color: #243849;
	}
</style>
