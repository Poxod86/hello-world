<template>
  <div class="display">
		<input v-model="operand1"/>
		{{ operator }}
		<input v-model="operand2"/>
		= {{ result }} <br>
		<button @click="operator = '+'">+</button>
		<button @click="operator = '-'">-</button>
		<button @click="operator = '*'">*</button>
		<button @click="operator = '/'">/</button>
		<button @click="operator = this.result">=</button>

	</div>
		
</template>

<script>

export default {
  name: 'App',
  	data() {
			return {
			operand1: 0,
			operand2: 0,
			operator: '+',
			result: 0
		}
	},
	methods: {
		getResult() {
			switch (operator) {
				case this.operator == '+':
					this.result = Number(this.operand1) + Number(this.operand2)
					break;
			
				default: result = "Error"
					break;
			}
		}
	}
}
</script>

<style>

</style>
