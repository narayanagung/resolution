<script setup>
import { RouterView } from "vue-router";
import TodoHeader from "./components/TodoHeader.vue";
</script>

<template>
	<TodoHeader />
	<RouterView />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap");
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
	height: -webkit-fill-available;
	scrollbar-width: thin;

	::-webkit-scrollbar {
		width: 5px;
		height: 5px;
	}

	::-webkit-scrollbar-track {
		background: transparent;
	}

	::-webkit-scrollbar-thumb {
		background: hsl(0, 0%, 66%);
		border-radius: 8px;
	}

	::-webkit-scrollbar-thumb:hover {
		background: hsl(0, 0%, 50%);
	}
}

body {
	height: -webkit-fill-available;
	background-color: hsl(0, 0%, 90%);
	color: hsl(0, 0%, 10%);

	@media (prefers-color-scheme: dark) {
		background-color: hsl(0, 0%, 10%);
		color: hsl(0, 0%, 95%);
	}

	background-image: radial-gradient(
		circle,
		hsla(334, 65%, 81%, 0.2) 0%,
		hsla(295, 28%, 76%, 0.2) 20%,
		hsla(263, 33%, 78%, 0.2) 48%,
		hsla(233, 41%, 79%, 0.2) 77%,
		hsla(212, 66%, 75%, 0.2) 100%
	);
	background-size: 200%;
}

.nav-wrap {
	margin: 0 auto;
}
</style>
