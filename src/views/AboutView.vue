<script setup>
import { Icon } from "@iconify/vue";
</script>

<template>
	<main>
		<h1>About</h1>
		<p>A basic to-do app that only needs to be checked once a year. Resolusi is here to remind you to accomplish your goals.</p>
		<h1>Notice</h1>
		<p>
			No account required but make sure to <strong>not</strong> use <strong>incognito mode</strong> if you want your list to be saved and persist;
			otherwise, it's going to be deleted as soon as you exit.
		</p>
		<h1>Tip</h1>
		<p>Bookmark this site for easier access to your list.</p>
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
	margin: 0 auto;
	padding: 0 1rem 1rem 1rem;

	@media screen and (max-width: 565px) {
		padding: 0.5rem 1rem 1rem 1rem;
	}

	h1 {
		margin-bottom: 0.5rem;
		font-size: 2rem;

		@media screen and (max-width: 565px) {
			font-size: 1.6rem;
		}
	}

	p {
		margin-bottom: 2rem;
		line-height: 1.8rem;
		font-size: medium;
		overflow-wrap: break-word;
		word-wrap: break-word;
		word-break: break-word;
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
