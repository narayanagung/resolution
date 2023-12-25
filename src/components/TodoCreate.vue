<script setup>
import { reactive } from "vue";

const emit = defineEmits(["create-todo"]);
const todoState = reactive({
	todo: "",
	invalid: null,
	errMsg: "",
});

const createTodo = () => {
	todoState.invalid = null;
	if (todoState.todo !== "") {
		emit("create-todo", todoState.todo);
		todoState.todo = "";
		return;
	}
	todoState.invalid = true;
	todoState.errMsg = "Value cannot be empty";
};
</script>

<template>
	<div
		class="input-wrap"
		:class="{ 'input-err': todoState.invalid }">
		<input
			type="text"
			v-model="todoState.todo" />
		<button @click="createTodo()">Create</button>
	</div>
	<small
		v-show="todoState.invalid"
		class="err-msg"
		>{{ todoState.errMsg }}</small
	>
</template>

<style lang="scss" scoped>
.input-wrap {
	display: flex;
	transition: 250ms ease;
	border: 2px solid #cacaca;

	&:focus-within {
		border: 2px solid #41b080;
	}

	&.input-err {
		border-color: hsla(0, 100%, 50%, 0.7);
	}

	input {
		width: 100%;
		padding: 8px 6px;
		border: none;

		&:focus {
			outline: none;
		}
	}

	button {
		padding: 8px 16px;
		border: none;
		cursor: pointer;

		&:hover {
			background-color: hsl(0, 0%, 90%);
			transition: 150ms ease-in-out;
		}
	}
}

.err-msg {
	margin: 0.5rem 0 0.5rem 0;
	color: hsla(0, 100%, 50%, 0.7);
	text-align: center;
}
</style>
