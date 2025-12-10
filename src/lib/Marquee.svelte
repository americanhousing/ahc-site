<script lang="ts">
	import { onMount, tick } from "svelte";

	type Props = {
		items: string[];
		speed?: number;
	};

	const { items, speed = 15 }: Props = $props();

	let measureContainer = $state<HTMLElement | undefined>(undefined);
	let windowWidth = $state(0);
	let itemsWidth = $state(0);

	let duplicateCount = $derived.by(() => {
		if (itemsWidth === 0) {
			return 2;
		}

		return Math.ceil(windowWidth / itemsWidth) + 2;
	});

	let animationDuration = $derived.by(() => {
		if (itemsWidth === 0) {
			return 10;
		}

		return itemsWidth / speed;
	});

	let containerStyle = $derived.by(() => {
		return `--items-width: ${itemsWidth}px; --duration: ${animationDuration}s`;
	});

	function didResizeWindow() {
		windowWidth = window.innerWidth;
		didMeasureItems();
	}

	function didMeasureItems() {
		if (measureContainer !== undefined) {
			itemsWidth = measureContainer.scrollWidth;
		}
	}

	onMount(async () => {
		didResizeWindow();
		await tick();
		didMeasureItems();
	});
</script>

<svelte:window onresize={didResizeWindow} />

<div
	class="pointer-events-none invisible absolute"
	bind:this={measureContainer}>
	<div class="flex gap-6">
		{#each items as item}
			<span class="whitespace-nowrap">{item}</span>
		{/each}
	</div>
</div>

<div class="h-[50px] overflow-hidden" style={containerStyle}>
	<div class="marquee-track text-driveway flex h-full items-center gap-6">
		{#each { length: duplicateCount } as _, i}
			{#each items as item}
				<span class="whitespace-nowrap">{item}</span>
			{/each}
		{/each}
	</div>
</div>

<style>
	.marquee-track {
		animation: marquee var(--duration) linear infinite;
		will-change: transform;
	}

	@keyframes marquee {
		from {
			transform: translateX(0);
		}
		to {
			transform: translateX(calc(-1 * var(--items-width)));
		}
	}
</style>
