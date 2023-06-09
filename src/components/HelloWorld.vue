<script setup lang="ts">
	import { ref } from "vue";

	defineProps<{ msg: string }>();

	const count = ref(0);
</script>

<template>
	<h1 class="text-3xl">{{ msg }}</h1>

	<div class="card">
		<button type="button" @click="count++">count is {{ count }}</button>
		<p>Welcome to Caddi!</p>
	</div>

	<p>
		Install
		<a href="https://github.com/vuejs/language-tools" target="_blank"
			>Volar</a
		>
		in your IDE for a better DX
	</p>
	<a href="https://github.com/rhughes42/caddi/wiki" class="read-the-docs"
		>Click here to learn more about the project.</a
	>
</template>

<style scoped>
	.read-the-docs {
		color: #888;
	}
</style>
