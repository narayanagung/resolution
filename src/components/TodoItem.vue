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
			title="Action">
			<Icon
				v-if="todo.isEditing"
				class="icon"
				icon="mdi:check-bold"
				color="#22ab7a"
				width="25"
				height="25"
				@click="$emit('edit-todo', index)" />
			<Icon
				v-else
				class="icon"
				icon="mdi:pencil"
				color="#097cca"
				width="25"
				height="25"
				@click="$emit('edit-todo', index)" />
			<Icon
				class="icon"
				icon="mdi:trash"
				color="#ff4c4c"
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
	background-color: #f5f5f5;
	box-shadow: 0 10px 13.5px -2.5px rgb(0 0 0 / 0.1), 0 4px 5px -3px rgb(0 0 0 / 0.1);

	&:hover {
		.todo-actions {
			opacity: 1;
		}
	}

	input[type="checkbox"] {
		appearance: none;
		width: 25px;
		height: 25px;
		background-color: hsla(154, 46%, 47%, 0.2);
		border-radius: 50%;
		cursor: pointer;

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
		transition: 150ms ease-in-out;

		.icon {
			cursor: pointer;
		}
	}
}
</style>
