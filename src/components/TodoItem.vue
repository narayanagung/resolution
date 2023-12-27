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
		<input title="Click to complete" type="checkbox" :checked="todo.isCompleted" @input="$emit('toggle-complete', index)" />
		<div class="todo">
			<input v-if="todo.isEditing" type="text" :value="todo.todo" @input="$emit('update-todo', $event.target.value, index)" />
			<span v-else :class="{ 'completed-todo': todo.isCompleted }">{{ todo.todo }}</span>
		</div>
		<div class="todo-actions" title="Action edit | delete">
			<Icon v-if="todo.isEditing" class="icon" icon="mdi:check-bold" width="25" height="25" @click="$emit('edit-todo', index)" />
			<Icon v-else class="icon" icon="mdi:pencil" width="25" height="25" @click="$emit('edit-todo', index)" />
			<Icon class="icon" icon="mdi:trash-can" width="25" height="25" @click="$emit('delete-todo', todo.id)" />
		</div>
	</li>
</template>

<style lang="scss" scoped>
li {
	display: flex;
	align-items: center;
	gap: 1rem;
	padding: 1rem;
	background-color: hsl(0, 0%, 100%);
	border-radius: 4px;
	box-shadow: 4px 4px 4px hsl(0, 0%, 53%);
	outline: 2px solid hsl(0, 0%, 50%);

	@media (prefers-color-scheme: dark) {
		background-color: hsl(0, 0%, 23%);
		box-shadow: 4px 4px 4px hsl(0, 0%, 13%);
	}

	&:hover {
		transition: 150ms ease-in-out;

		.todo-actions {
			opacity: 1;
			transition: 150ms ease-in-out;
		}
	}

	input[type="checkbox"] {
		width: 25px;
		height: 25px;
		cursor: pointer;
	}

	.todo {
		flex: 1;

		.completed-todo {
			text-decoration: line-through;
		}

		input[type="text"] {
			width: 100%;
			padding: 0.5rem 0.5rem;
			border: 1px solid hsl(0, 0%, 0%);
			border-radius: 4px;
			border: 1px solid hsl(154, 46%, 47%);

			&:focus {
				outline: none;
			}
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
