<script setup>
import TodoCreate from "@/components/TodoCreate.vue";
import TodoItem from "@/components/TodoItem.vue";
import { computed, ref, watch } from "vue";
import { uid } from "uid";
import { vAutoAnimate } from "@formkit/auto-animate";
import { formatDate } from "@vueuse/core";

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
		<h1>What will you accomplish this year?</h1>
		<TodoCreate @create-todo="createTodo" />
		<ul v-auto-animate v-if="todoList.length > 0" class="todo-list">
			<TodoItem
				v-for="(todo, index) in todoList"
				:todo="todo"
				:index="index"
				@toggle-complete="toggleTodoComplete"
				@edit-todo="toggleEditTodo"
				@update-todo="updateTodo"
				@delete-todo="deleteTodo"
			/>
		</ul>
		<div class="msg" v-else>
			<p>No goals yet... It's ok; no pressure.</p>
			<img title="Ladida~ take your time~" src="../assets/init.png" alt="Yotsuba goals" />
		</div>
		<div class="msg" v-if="todoCompleted && todoList.length > 0">
			<p>Well done! You have completed all of your {{ formatDate(new Date(), "YYYY") }} Resolution!</p>
			<img title="Respect" src="../assets/completed.png" alt="Yotsuba complete" />
		</div>
	</main>
</template>

<style lang="scss" scoped>
main {
	display: flex;
	flex-direction: column;
	max-width: 35rem;
	margin: 0 auto;
	padding: 1rem;

	h1 {
		margin-bottom: 2rem;
		text-align: left;
		line-height: 4rem;
		font-weight: 800;
		font-size: 2.5rem;
		text-transform: initial;
	}

	.msg {
		margin: 2rem auto 0 auto;
		text-align: center;
		background-color: hsla(0%, 0%, 50%, 0.1);
		padding: 2rem 9rem;
		border-radius: 4px;

		img {
			margin-top: 1rem;
			max-width: 10rem;
		}
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
