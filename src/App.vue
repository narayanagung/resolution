<script setup>
import { RouterView } from "vue-router";
import TodoHeader from "./components/TodoHeader.vue";
</script>

<template>
	<TodoHeader />
	<RouterView />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&display=swap");
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
	@media (prefers-color-scheme: dark) {
		color: #fafafa;
	}
	scrollbar-width: thin;

	::-webkit-scrollbar {
		width: 5px;
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
}

body {
	background-color: hsl(0, 0%, 95%);
	@media (prefers-color-scheme: dark) {
		background-color: hsl(0, 0%, 10%);
	}
	background-image: radial-gradient(
		circle,
		hsla(334, 65%, 81%, 0.3) 0%,
		hsla(295, 28%, 76%, 0.3) 20%,
		hsla(263, 33%, 78%, 0.3) 48%,
		hsla(233, 41%, 79%, 0.3) 77%,
		hsla(212, 66%, 75%, 0.3) 100%
	);
	background-size: 300%;
	animation: body-animate 20s infinite;

	@keyframes body-animate {
		0% {
			background-position: right;
		}
		50% {
			background-position: left;
		}
		100% {
			background-position: right;
		}
	}
}

.nav-wrap {
	max-width: 0 auto;
	margin: 0 auto;

	@media screen and (min-width: 565px) {
		max-width: 0 auto;
	}
}
</style>
