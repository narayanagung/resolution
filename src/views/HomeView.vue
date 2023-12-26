<script setup>
import TodoCreate from "@/components/TodoCreate.vue";
import TodoItem from "@/components/TodoItem.vue";
import { computed, ref, watch } from "vue";
import { uid } from "uid";

const todoList = ref([]);

watch(
	todoList,
	() => {
		setTodoListLocalStorage();
	},
	{
		deep: true,
	}
);

const todoCompleted = computed(() => {
	return todoList.value.every((todo) => todo.isCompleted);
});

const fetchTodoList = () => {
	const savedTodoList = JSON.parse(localStorage.getItem("todoList"));
	if (savedTodoList) {
		todoList.value = savedTodoList;
	}
};

fetchTodoList();

const setTodoListLocalStorage = () => {
	localStorage.setItem("todoList", JSON.stringify(todoList.value));
};

const createTodo = (todo) => {
	todoList.value.push({
		id: uid(),
		todo,
		isCompleted: null,
		isEditing: null,
	});
};

const toggleTodoComplete = (todoPos) => {
	todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
};

const toggleEditTodo = (todoPos) => {
	todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing;
};

const updateTodo = (todoVal, todoPos) => {
	todoList.value[todoPos].todo = todoVal;
};

const deleteTodo = (todoId) => {
	todoList.value = todoList.value.filter((todo) => todo.id !== todoId);
};
</script>

<template>
	<main>
		<h1>What will you accomplished this year?</h1>
		<TodoCreate @create-todo="createTodo" />
		<h4
			class="all-clear"
			v-if="todoCompleted && todoList.length > 0">
			Mission All Clear! you have completed all of your goals!
		</h4>
		<ul
			v-if="todoList.length > 0"
			class="todo-list">
			<TodoItem
				v-for="(todo, index) in todoList"
				:todo="todo"
				:index="index"
				@toggle-complete="toggleTodoComplete"
				@edit-todo="toggleEditTodo"
				@update-todo="updateTodo"
				@delete-todo="deleteTodo" />
		</ul>
		<h4
			class="todo-init-msg"
			v-else>
			Clueless? Create your own todo's now!
		</h4>
	</main>
</template>

<style lang="scss" scoped>
main {
	display: flex;
	flex-direction: column;
	max-width: 35rem;
	width: 100%;
	margin: 0 auto;
	padding: 1rem;

	h1 {
		margin-bottom: 1rem;
	}

	h4 {
		margin: 2rem 0 1rem 0;
		text-align: center;
	}

	.todo-list {
		display: flex;
		flex-direction: column;
		list-style: none;
		margin-top: 1rem;
		gap: 1rem;
	}
}
</style>
