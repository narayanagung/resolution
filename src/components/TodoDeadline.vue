<script setup>
import { ref, onMounted } from "vue";

const targetDate = new Date(new Date().getFullYear() + 1, 0, 1);

const formattedCountdown = ref("");

const updateCountdown = () => {
	const now = new Date();
	const difference = targetDate - now;

	const days = Math.floor(difference / (1000 * 60 * 60 * 24));
	const hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
	const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
	const seconds = Math.floor((difference % (1000 * 60)) / 1000);

	formattedCountdown.value = `${days}D ${hours}H ${minutes}m ${seconds}s`;
};

onMounted(() => {
	updateCountdown();
	setInterval(updateCountdown, 1000);
});
const currentDate = new Date();
const currentYear = currentDate.getFullYear();
const nextYear = currentYear + 1;
</script>

<template>
	<div class="time-wrap">
		<h1 title="Better hurry">{{ formattedCountdown }}</h1>
		<h3 title="Better hurry">until {{ nextYear }}</h3>
	</div>
</template>

<style lang="scss" scoped>
.time-wrap {
	margin-bottom: 1rem;

	h3 {
		color: gray;
	}
}
@media screen and (max-width: 565px) {
	h1 {
		font-size: 1.7rem;
		text-align: center;
	}

	h3 {
		text-align: center;
	}
}
</style>
