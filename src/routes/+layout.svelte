<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<title>The American Housing Corporation</title>
</svelte:head>

{@render children()}
