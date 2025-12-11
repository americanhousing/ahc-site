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
	let currentIndex = $state<number>(0);

	function calculatePadding() {
		const maxWidth = 1392;
		const windowWidth = window.innerWidth;

		if (windowWidth > maxWidth) {
			horizontalPadding = Math.max((windowWidth - maxWidth) / 2, 24.0);
		} else {
			horizontalPadding = 24.0;
		}
	}

	function scrollToItem(index: number) {
		if (scroller === undefined) {
			return;
		}

		const itemElements = scroller.children;

		if (index < 0 || index >= itemElements.length) {
			return;
		}

		const item = itemElements[index] as HTMLElement;
		const itemWidth = item.offsetWidth;
		const viewportWidth = window.innerWidth;
		const itemCenter = item.offsetLeft + itemWidth / 2;
		const targetScrollLeft = itemCenter - viewportWidth / 2;

		scroller.scrollTo({
			left: targetScrollLeft,
			behavior: "smooth"
		});

		currentIndex = index;
	}

	function didClickItem(index: number) {
		scrollToItem(index);
	}

	function didPressKey(event: KeyboardEvent) {
		if (scroller === undefined) {
			return;
		}

		const scrollerRect = scroller.getBoundingClientRect();
		const isScrollerVisible =
			scrollerRect.top < window.innerHeight && scrollerRect.bottom > 0;

		if (isScrollerVisible === false) {
			return;
		}

		if (event.key === "ArrowLeft") {
			event.preventDefault();
			scrollToItem(Math.max(0, currentIndex - 1));
		}

		if (event.key === "ArrowRight") {
			event.preventDefault();
			scrollToItem(Math.min(items.length - 1, currentIndex + 1));
		}
	}

	function didResizeWindow() {
		calculatePadding();
	}

	onMount(() => {
		calculatePadding();
	});
</script>

<svelte:window onresize={didResizeWindow} onkeydown={didPressKey} />

<div
	bind:this={scroller}
	class="scrollbar-none hidden flex-nowrap gap-6 overflow-x-auto md:flex"
	style="padding-left: {horizontalPadding}px; padding-right: {horizontalPadding}px;">
	{#each items as item, index}
		<button
			type="button"
			onclick={() => didClickItem(index)}
			class="bg-driveway/20 relative h-[664px] min-w-[1116px] cursor-pointer rounded-[2px]">
			{#if item.image !== undefined}
				<img
					src={item.image}
					alt=""
					class="h-full w-full rounded-[2px] object-cover" />
			{/if}
			<div
				class="bg-cumulus/20 absolute bottom-6 left-6 flex w-auto gap-2 rounded-[2px] px-6 py-4 font-medium backdrop-blur-lg">
				<span class="text-cumulus">{item.year}</span>
				<span class="text-driveway">{item.text}</span>
			</div>
		</button>
	{/each}
</div>
