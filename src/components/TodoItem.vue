<script setup>
import { Icon } from "@iconify/vue";

const props = defineProps({
	todo: {
		type: Object,
		required: true,
	},
	index: {
		type: Number,
		required: true,
	},
});

defineEmits(["toggle-complete", "edit-todo", "update-todo", "delete-todo"]);
</script>

<template>
	<li>
		<input
			title="Click to complete"
			type="checkbox"
			:checked="todo.isCompleted"
			@input="$emit('toggle-complete', index)" />
		<div class="todo">
			<input
				v-if="todo.isEditing"
				type="text"
				:value="todo.todo"
				@input="$emit('update-todo', $event.target.value, index)" />
			<span
				v-else
				:class="{ 'completed-todo': todo.isCompleted }"
				>{{ todo.todo }}</span
			>
		</div>
		<div
			class="todo-actions"
			title="Action edit | delete">
			<Icon
				v-if="todo.isEditing"
				class="icon"
				icon="mdi:check-bold"
				color="#41af7f"
				width="25"
				height="25"
				@click="$emit('edit-todo', index)" />
			<Icon
				v-else
				class="icon"
				icon="mdi:pencil"
				color="#56a3ff"
				width="25"
				height="25"
				@click="$emit('edit-todo', index)" />
			<Icon
				class="icon"
				icon="mdi:trash"
				color="#ff0000"
				width="25"
				height="25"
				@click="$emit('delete-todo', todo.id)" />
		</div>
	</li>
</template>

<style lang="scss" scoped>
li {
	display: flex;
	align-items: center;
	gap: 1rem;
	padding: 1rem 0.5rem;
	background-color: hsl(0, 0%, 96%);

	@media (prefers-color-scheme: dark) {
		background-color: hsl(0, 0%, 23%);
	}

	&:hover {
		.todo-actions {
			opacity: 1;
			transition: 150ms ease-in-out;
		}
	}

	input[type="checkbox"] {
		appearance: none;
		width: 25px;
		height: 25px;
		background-color: hsl(0, 0%, 80%);
		border-radius: 50%;
		cursor: pointer;

		@media (prefers-color-scheme: dark) {
			background-color: hsl(0, 0%, 50%);
		}

		&:checked {
			background-color: hsl(154, 46%, 47%);
		}
	}

	.todo {
		flex: 1;

		.completed-todo {
			text-decoration: line-through;
		}

		input[type="text"] {
			width: 100%;
			padding: 0.5rem 0.5rem;
			border: 2px solid #41b080;
		}
	}

	.todo-actions {
		display: flex;
		gap: 0.5rem;
		opacity: 0;

		.icon {
			cursor: pointer;
		}
	}
}
</style>
