<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
	<header>
		<nav class="wrap">
			<div class="branding">
				<img
					title="Logo"
					src="../assets/logo.png"
					alt="Vue 3 Logo" />
				<h3 title="Todos">Todos</h3>
			</div>
			<ul class="nav-routes">
				<RouterLink
					to="/"
					title="Homepage"
					>Home</RouterLink
				>
				<RouterLink
					to="/about"
					title="About this app"
					>About</RouterLink
				>
			</ul>
		</nav>
	</header>
</template>

<style lang="scss" scoped>
header {
	background-color: #f1f1f1;

	nav {
		display: flex;
		align-items: center;
		padding: 1rem 1.5rem;

		.branding {
			display: flex;
			align-items: center;
			gap: 0.5rem;
			list-style: none;

			img {
				max-width: 50px;
			}
		}

		.nav-routes {
			display: flex;
			flex: 1;
			justify-content: flex-end;
			list-style: none;
			align-items: center;
			gap: 1rem;

			a {
				text-decoration: none;
				color: inherit;

				&:hover {
					text-decoration: underline;
				}
			}
		}
	}
}
</style>
