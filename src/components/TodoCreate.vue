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
	<div class="input-wrap" :class="{ 'input-err': todoState.invalid }">
		<input type="text" placeholder="Add your goals" v-model="todoState.todo" />
		<button title="Add goals to the list" @click="createTodo()">Add</button>
	</div>
	<small v-show="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</small>
</template>

<style lang="scss" scoped>
.input-wrap {
	display: flex;
	transition: 250ms ease;
	outline: 2px solid hsl(154, 46%, 47%);
	box-shadow: 4px 4px 4px hsl(0, 0%, 53%);

	@media (prefers-color-scheme: dark) {
		box-shadow: 4px 4px 4px hsl(0, 0%, 13%);
	}

	&.input-err {
		border-color: hsla(0, 100%, 50%, 0.9);

		button {
			background-color: hsla(0, 100%, 50%, 0.9);

			&:hover {
				background-color: hsla(0, 100%, 60%, 1);
			}
		}
	}

	input {
		width: 100%;
		padding: 1rem;
		border: none;

		&:focus {
			outline: none;
		}
	}

	button {
		background-color: hsl(154, 46%, 47%);
		padding: 0.5rem 1.5rem;
		border: none;
		cursor: pointer;
		font-weight: bold;
		color: white;
		box-shadow: 4px 4px 4px hsl(0, 0%, 53%);

		@media (prefers-color-scheme: dark) {
			box-shadow: 4px 4px 4px hsl(0, 0%, 13%);
		}

		&:hover {
			background-color: hsl(154, 46%, 55%);
			transition: 150ms ease-in-out;
		}
	}
}

.err-msg {
	margin: 0.5rem 0 0.5rem 0;
	color: hsl(0, 100%, 55%);
	text-align: center;
}
</style>
