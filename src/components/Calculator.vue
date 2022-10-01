<script setup>
import Key from './Key.vue'
import Screen from './Screen.vue'
import Error from './Error.vue'
</script>

<script >
export default {
	data() {
		return {
			firstValue: "",
			secondValue: "",
			operation: null,
			result: "",
			isResolved: false,
			error: "",
			hasErrors: false,
			keys: [
				{
					value: "C",
					class: "bg-yellow text-black",
					operation: this.clearValue
				},
				{
					value: "/",
					class: "bg-grey text-black",
					operation: this.addOperator
				},
				{
					value: "X",
					class: "bg-grey text-black",
					operation: this.addOperator
				},
				{
					value: "-",
					class: "minus bg-magenta text-black",
					operation: this.addOperator
				},
				{
					value: "1",
					class: "",
					operation: this.addValue
				},
				{
					value: "2",
					class: "",
					operation: this.addValue
				},
				{
					value: "3",
					class: "",
					operation: this.addValue
				},
				{
					value: "4",
					class: "",
					operation: this.addValue
				},
				{
					value: "5",
					class: "",
					operation: this.addValue
				},
				{
					value: "6",
					class: "",
					operation: this.addValue
				},
				{
					value: "+",
					class: "plus bg-grey text-black",
					operation: this.addOperator
				},
				{
					value: "7",
					class: "",
					operation: this.addValue
				},
				{
					value: "8",
					class: "",
					operation: this.addValue
				},
				{
					value: "9",
					class: "",
					operation: this.addValue
				},
				{
					value: "0",
					class: "zero",
					operation: this.addValue
				},
				{
					value: "=",
					class: "equal bg-magenta text-black",
					operation: this.evaluate
				},
			]
		}
	},
	methods: {
		addValue: function (value) {
			if (this.isResolved) this.clearValue();

			value = value.toString();

			if (this.operation == null) {
				this.firstValue += value;
			} else {
				this.secondValue += value;
			}

			this.resetError();
		},
		clearValue: function () {
			this.firstValue = "";
			this.secondValue = "";
			this.operation = null;
			this.result = "";
			this.isResolved = false;

			this.resetError();
		},
		addOperator: function (operator) {
			if (operator === "X") operator = '*'
			this.operation = operator;
		},
		evaluate: function () {

			if (!this.checkErrors()) {
				this.hasErrors = true;
				return;
			}

			this.result = eval(this.firstValue + this.operation + this.secondValue);
			this.isResolved = true;
		},
		checkErrors: function () {
			if (this.firstValue === "") {
				this.error = "Introduce el primer número";
				return false;
			}

			if (this.firstValue !== "" && this.operation !== "" && this.firstValue === "") {
				this.error = "Introduce el segundo número";
				return false;
			}

			return true;
		},
		resetError: function () {
			this.error = "";
			this.hasErrors = false;
		}
	}
}
</script>

<template>
	<div class="layout">
		<Screen>
			<template #keyName>
				{{firstValue == ""? 'Introduce valores': firstValue}} {{operation}} {{secondValue}} {{result ?
				'=': ''}} {{result}}
			</template>
		</Screen>
		<Key v-for="key in this.keys" :class="key.class" @click="key.operation(key.value)">
			<template #keyName>{{key.value}}</template>
		</Key>
		<Error v-if="hasErrors">
			<template #keyName>
				{{error}}
			</template>
		</Error>
	</div>
</template>

<style>
.layout {
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	gap: 2px;
	margin-top: 2rem;
}
</style>
