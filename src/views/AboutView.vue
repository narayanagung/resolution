<script setup>
import { Icon } from "@iconify/vue";
</script>

<template>
	<main>
		<h1>About</h1>
		<p>
			It's easy to lose track of our goals. Whether it's a career milestone, a personal growth endeavor, or simply a task you've been postponing,
			<strong>Resolusi</strong> is here to remind you to reach those goals.
		</p>
		<h1>Notice</h1>
		<p>
			Make sure to not use <strong>"incognito mode"</strong> if you want your list to be saved and persist in the browser; otherwise, it's going to be
			deleted as soon as you exit the browser.
		</p>
		<ul class="credit">
			<li><small>Made with 💟 by narayanagung</small></li>
			<li>
				<a title="Github profile" href="https://github.com/narayanagung" target="_blank"><Icon icon="bi:github" width="20" height="20" /></a>
			</li>
			<li>
				<a title="Instagram social" href="https://instagram.com/narayanagung" target="_blank"><Icon icon="bi:instagram" width="20" height="20" /></a>
			</li>
		</ul>
	</main>
</template>

<style lang="scss" scoped>
main {
	display: grid;
	align-items: center;
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

	.credit {
		display: flex;
		justify-content: flex-end;
		list-style-type: none;
		gap: 1rem;
		margin-top: 1rem;

		li a {
			color: inherit;

			&:hover {
				color: hsl(200, 100%, 49%);
				transition: 150ms ease-in-out;
			}
		}
	}
}
</style>
