<script setup>
import { Icon } from "@iconify/vue";
</script>

<template>
	<main>
		<h1>About</h1>
		<p>
			In the hustle and bustle of post-modern life, it's easy to lose track of our goals. Whether it's a career milestone, a personal growth endeavor, or
			simply a task you've been postponing, Resolution is here to ensure you to reach those goals.
		</p>
		<ul class="credit">
			<li>
				<a
					title="Github"
					href="https://github.com/narayanagung/resolution"
					target="_blank"
					><Icon
						icon="mdi:github"
						width="25"
						height="25"
				/></a>
			</li>
			<li>
				<a
					title="Instagram"
					href="https://www.instagram.com/narayanagung"
					target="_blank"
					><Icon
						icon="mdi:instagram"
						width="25"
						height="25"
				/></a>
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
		margin-bottom: 1rem;
	}

	p {
		margin-bottom: 1.5rem;
		text-wrap: balance;
	}

	.credit {
		display: flex;
		justify-content: flex-end;
		list-style-type: none;
		gap: 1rem;

		li a {
			color: inherit;
		}
	}
}
</style>
