<script setup>
import { RouterLink } from "vue-router";
import { formatDate } from "@vueuse/core";
</script>

<template>
	<header>
		<nav class="nav-wrap">
			<div class="branding">
				<img title="Logo" src="../assets/logo.png" alt="Vue 3 Logo" />
				<RouterLink class="router-link" to="/" title="Homepage">Resolusi {{ formatDate(new Date(), "YYYY") }}</RouterLink>
			</div>
			<ul class="nav-routes">
				<RouterLink to="/about" title="About this app">About</RouterLink>
			</ul>
		</nav>
	</header>
</template>

<style lang="scss" scoped>
header {
	nav {
		display: flex;
		align-items: center;
		padding: 1rem;

		.branding {
			display: flex;
			align-items: center;
			gap: 0.5rem;
			list-style: none;

			img {
				max-width: 35px;
			}
			.router-link {
				text-decoration: none;
				color: hsl(0, 0%, 10%);
				font-size: large;
				font-weight: 600;

				@media (prefers-color-scheme: dark) {
					color: hsl(0, 0%, 98%);
				}

				&:hover {
					color: hsl(200, 100%, 49%);
					transition: 150ms ease-in-out;
				}
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
				font-weight: 600;

				&:hover {
					color: hsl(200, 100%, 49%);
					transition: 150ms ease-in-out;
				}
			}
		}
	}
}
</style>
