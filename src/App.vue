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

*,
::after,
::before {
	font-family: "Poppins", sans-serif;
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

:root {
	color-scheme: light dark;
}

html {
	scrollbar-width: thin;

	::-webkit-scrollbar {
		width: 10px;
		height: 5px;
	}

	::-webkit-scrollbar-track {
		background: hsla(0, 0%, 0%, 0);
	}

	::-webkit-scrollbar-thumb {
		background: hsl(0, 0%, 66%);
		border-radius: 8px;
	}

	::-webkit-scrollbar-thumb:hover {
		background: hsl(0, 0%, 50%);
	}

	@media (prefers-color-scheme: dark) {
		color: #fafafa;
	}
}

.nav-wrap {
	max-width: 35rem;
	margin: 0 auto;

	@media screen and (min-width: 565px) {
		max-width: 100rem;
	}
}

img {
	display: block;
}
</style>
