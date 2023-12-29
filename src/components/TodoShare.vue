<script setup>
import { Icon } from "@iconify/vue";
import swal from "sweetalert";

const share = () => {
	if (navigator.share) {
		navigator.share({
			text: "Keep track of your goals with Resolusi!",
			url: "https://resolussy.vercel.app",
			title: "Resolusi - List Your Yearly Goals",
		});
	} else {
		navigator.clipboard.writeText("Resolusi - List Your Yearly Goals\nhttps://resolussy.vercel.app \nKeep track of your goals with Resolusi!");
		swal("Message copied to clipboard", "Thanks for sharing 🙏");
	}
};
</script>

<template>
	<div class="share-wrap">
		<ul>
			<li>
				<button @click="share" class="share" title="Share it!">Invite others <Icon icon="ic:round-share" width="20" height="20" /></button>
			</li>
		</ul>
	</div>
</template>

<style lang="scss" scoped>
.share-wrap {
	display: flex;
	justify-content: center;
	margin-top: auto;

	ul {
		display: flex;
		list-style-type: none;
		gap: 0.5rem;
		margin: 1rem 0;

		.share {
			display: flex;
			align-items: center;
			padding: 0.4rem 1rem;
			text-decoration: none;
			background-color: hsl(154, 46%, 47%);
			border-radius: 16px;
			gap: 0.3rem;
			font-size: medium;
			font-weight: bold;
			color: hsl(0, 0%, 95%);
			border: none;
			cursor: pointer;
			margin-top: 1rem;

			&:hover {
				background-color: hsl(154, 46%, 55%);
				transition: 150ms ease-in-out;
			}
		}
	}
}
</style>
