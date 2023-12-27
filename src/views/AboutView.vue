<script setup>
import { Icon } from "@iconify/vue";
</script>

<template>
	<main>
		<h1>About</h1>
		<p>
			It's easy to lose track of our goals. Whether it's a career milestone, a personal growth endeavor, or simply a task you've been postponing,
			Resolution is here to remind you to reach those goals.
		</p>
		<h1>Notice</h1>
		<p>
			Make sure to not use "incognito mode" if you want the list to be saved and persist in your browser; otherwise, it's going to be deleted as soon as
			you exit the browser.
		</p>
		<h1>Notes</h1>
		<p class="quote">"basically a modified version of basic todo webapp"</p>
		<ul class="credit">
			<li>
				<a title="Github" href="https://github.com/narayanagung" target="_blank"><Icon icon="mdi:github" width="25" height="25" /></a>
			</li>
			<li><small>Made with 💟 by narayanagung</small></li>
		</ul>
	</main>
</template>

<style lang="scss" scoped>
main {
	display: flex;
	flex-direction: column;
	max-width: 35rem;
	width: 100%;
	margin: 0 auto;
	padding: 1rem;

	h1 {
		margin-bottom: 0.5rem;
	}

	p {
		margin-bottom: 2rem;
		line-height: 1.7rem;
	}

	.quote {
		font-weight: 600;
	}

	.credit {
		display: flex;
		justify-content: flex-end;
		list-style-type: none;
		gap: 1rem;
		margin-top: 1rem;

		@media screen and (max-width: 350px) {
			gap: 0.5rem;
		}

		li a {
			color: inherit;
		}
	}
}
</style>
