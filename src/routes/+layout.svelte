<script lang="ts">
	import { onNavigate } from '$app/navigation';
	import '../app.css';

	let { children } = $props();

	onNavigate(function (navigation) {
		if (document.startViewTransition === undefined) {
			return;
		}

		return new Promise(function (resolve) {
			document.startViewTransition(async function () {
				resolve();
				await navigation.complete;
			});
		});
	});
</script>

<svelte:head>
	<title>The American Housing Corporation</title>
</svelte:head>

{@render children()}
