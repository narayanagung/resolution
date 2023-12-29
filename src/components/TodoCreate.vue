<script setup>
import { reactive, ref } from "vue";

const emit = defineEmits(["create-todo"]);
const todoState = reactive({
	todo: "",
	invalid: null,
	errMsg: "",
});

const maxCharacter = 255;
const todoInput = ref(null);

const createTodo = () => {
	todoState.invalid = null;
	if (todoState.todo !== "") {
		if (todoState.todo.length > maxCharacter) {
			todoState.invalid = true;
			todoState.errMsg = `Character limit exceeded. Maximum ${maxCharacter} characters allowed.`;
			return;
		}
		emit("create-todo", todoState.todo);
		todoState.todo = "";
		if (todoInput.value) {
			todoInput.value.focus();
		}
		return;
	}
	todoState.invalid = true;
	todoState.errMsg = "Value cannot be empty.";
};
</script>

<template>
	<div class="input-wrap" :class="{ 'input-err': todoState.invalid }">
		<input title="Type here" @keyup.enter="createTodo" ref="todoInput" v-model="todoState.todo" type="text" name="create" placeholder="Add your goal" />
		<button title="Add goal button" @click="createTodo">Add</button>
	</div>
	<small v-show="todoState.invalid" class="err-msg">{{ todoState.errMsg }}</small>
</template>

<style lang="scss" scoped>
.input-wrap {
	display: flex;
	transition: 250ms ease;
	outline: 2px solid hsl(154, 46%, 47%);

	&.input-err {
		outline: 2px solid hsla(0, 100%, 50%, 0.9);

		button {
			background-color: hsla(0, 100%, 50%, 0.9);
			outline: 2px solid hsla(0, 100%, 50%, 0.9);

			&:hover {
				background-color: hsla(0, 100%, 65%, 1);
				outline: 2px solid hsla(0, 100%, 65%, 1);
			}
		}
	}

	input {
		width: 100%;
		padding: 1rem;
		border: none;
		font-size: medium;

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
		font-size: medium;
		color: hsl(0, 0%, 100%);
		outline: 2px solid hsl(154, 46%, 47%);

		&:hover {
			background-color: hsl(154, 46%, 55%);
			outline: 2px solid hsl(154, 46%, 55%);
			transition: 150ms ease-in-out;
		}
	}
}

.err-msg {
	margin: 0.5rem 0 0.5rem 0;
	color: hsla(0, 100%, 50%, 0.9);
	text-align: center;
}
</style>
