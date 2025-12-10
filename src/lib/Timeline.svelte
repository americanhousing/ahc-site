<script lang="ts">
	import { onMount } from "svelte";

	type TimelineItem = {
		year: string;
		text: string;
		image?: string;
	};

	type Props = {
		items: TimelineItem[];
	};

	const { items }: Props = $props();

	let scroller = $state<HTMLElement | undefined>(undefined);
	let horizontalPadding = $state<number>(0);

	function calculatePadding() {
		const maxWidth = 1392;
		const windowWidth = window.innerWidth;

		if (windowWidth > maxWidth) {
			horizontalPadding = (windowWidth - maxWidth) / 2;
		} else {
			horizontalPadding = 0;
		}
	}

	function didResizeWindow() {
		calculatePadding();
	}

	onMount(() => {
		calculatePadding();
	});
</script>

<svelte:window onresize={didResizeWindow} />

<div
	bind:this={scroller}
	class="scrollbar-none hidden flex-nowrap gap-6 overflow-x-auto md:flex"
	style="padding-left: {horizontalPadding}px; padding-right: {horizontalPadding}px;">
	{#each items as item}
		<div
			class="bg-driveway relative h-[664px] min-w-[1116px] rounded-[2px]">
			{#if item.image !== undefined}
				<img
					src={item.image}
					alt=""
					class="h-full w-full rounded-[2px] object-cover" />
			{/if}
			<div
				class="bg-cumulus/20 absolute bottom-6 left-6 flex w-auto gap-2 rounded-[2px] px-6 py-4 backdrop-blur-lg">
				<span class="text-cumulus">{item.year}</span>
				<span class="text-cumulus">{item.text}</span>
			</div>
		</div>
	{/each}
</div>
