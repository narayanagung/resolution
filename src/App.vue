<script setup>
import { RouterView } from "vue-router";
import TodoHeader from "./components/TodoHeader.vue";
</script>

<template>
	<TodoHeader />
	<RouterView />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;700&display=swap");

* {
	font-family: "Poppins", sans-serif;
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

html {
	scrollbar-width: thin;

	::-webkit-scrollbar {
		width: 5px;
		height: 5px;
	}

	::-webkit-scrollbar-track {
		background: rgb(0, 0, 0, 0);
		border-radius: 8px;
	}

	::-webkit-scrollbar-thumb {
		background: darkgrey;
		border-radius: 8px;
	}

	::-webkit-scrollbar-thumb:hover {
		background: gray;
	}
}

.wrap {
	max-width: 100vw;
	margin: 0 auto;
}
</style>
