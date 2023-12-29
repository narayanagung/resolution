<script setup>
import TodoCreate from "@/components/TodoCreate.vue";
import TodoItem from "@/components/TodoItem.vue";
import TodoShare from "@/components/TodoShare.vue";
import TodoDeadline from "@/components/TodoDeadline.vue";
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
		<h1 v-show="todoList.length < 1">What will you accomplish this year?</h1>
		<TodoDeadline v-if="todoList.length > 0" />
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
		<div class="msg-init" v-else>
			<p>Can't think of one? It's ok, no pressure...</p>
			<img title="Take your time~" src="../assets/init.webp" alt="Manga character by Kiyohiko Azuma 'Yotsuba Koiwai'" />
		</div>
		<div class="msg-complete" v-if="todoCompleted && todoList.length > 0">
			<p>You have completed all of your {{ formatDate(new Date(), "YYYY") }} resolutions! Good job.</p>
			<img title="Respect" src="../assets/completed.webp" alt="Manga character by Kiyohiko Azuma 'Yotsuba Koiwai'" />
		</div>
		<TodoShare />
	</main>
</template>

<style lang="scss" scoped>
main {
	display: flex;
	flex-direction: column;
	max-width: 35rem;
	margin: 0 auto;
	min-height: 90dvh;
	min-height: 90vh;
	padding-inline: 1rem;

	h1 {
		margin-bottom: 2rem;
		text-align: left;
		line-height: 3.5rem;
		font-weight: 700;
		font-size: 2.5rem;

		@media screen and (max-width: 565px) {
			font-size: 1.7rem;
			line-height: 3rem;
			text-align: center;
			margin-bottom: 1rem;
		}
	}

	.msg-init {
		margin: 2rem auto 0 auto;
		text-align: center;
		border-radius: 4px 4px 0 0;
		padding: 1rem;
		font-weight: 600;
		font-size: large;

		@media screen and (max-width: 565px) {
			margin: 1rem auto 0 auto;
		}

		img {
			margin-top: 1rem;
			max-width: 8rem;
		}
	}
	.msg-complete {
		margin: 2rem auto 0 auto;
		text-align: center;
		border-radius: 4px;
		padding: 1rem;
		font-weight: 600;
		font-size: large;

		@media screen and (max-width: 565px) {
			margin: 1rem auto 0 auto;
		}

		span {
			color: hsl(0, 94%, 48%);
			opacity: 0.1;
		}

		p {
			text-wrap: balance;
		}

		img {
			margin-top: 1rem;
			max-width: 8rem;
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
