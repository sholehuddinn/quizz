<script setup>
import { RouterView } from 'vue-router';
</script>

<template>
	<main class="container">
		<RouterView />
	</main>
</template>

<style scoped>
	.container {
		width: 90%;
    margin: 0 auto;
		display: flex;
		justify-content: center;
	}
</style>