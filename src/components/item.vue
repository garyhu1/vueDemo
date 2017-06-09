<template>
	<div>
		<p class="test">{{ item }}</p>
	</div>
</template>

<script>
	export default {
		props: ['item']
	}
</script>

<style>
	.test {
		color: red;
		font-size: 1em;
	}
</style>