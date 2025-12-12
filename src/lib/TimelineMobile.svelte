<script lang="ts">
	import { onDestroy } from "svelte";

	type TimelineItem = {
		year: string;
		text: string;
		image?: string;
	};

	type Props = {
		items: TimelineItem[];
	};

	const { items }: Props = $props();

	const slideDurationMs = 400;
	const autoAdvanceDelayMs = 5000;

	let container = $state<HTMLElement | undefined>(undefined);
	let currentIndex = $state<number>(0);
	let targetIndex = $state<number>(0);
	let slideOffset = $state<number>(0);
	let isSliding = $state<boolean>(false);
	let transitionsEnabled = $state<boolean>(true);
	let isVisible = $state<boolean>(false);
	let progress = $state<number>(0);

	let slideTimeout: ReturnType<typeof setTimeout> | undefined = undefined;
	let autoAdvanceAnimationFrame: number | undefined = undefined;
	let autoAdvanceStartTime: number | undefined = undefined;
	let visibilityObserver: IntersectionObserver | undefined = undefined;

	let length = $derived(items.length);

	let visibleOffsets = $derived.by(() => {
		if (length < 3) {
			return [-1, 0, 1];
		}

		return [-1, 0, 1];
	});

	let visibleItems = $derived.by(() => {
		if (length === 0) {
			return [];
		}

		return visibleOffsets.map((offset) => {
			const index = normalizeIndex(currentIndex + offset);
			const effectiveOffset = offset + slideOffset;
			const translateX = effectiveOffset * 100;

			return {
				key: `${index}-${offset}`,
				offset,
				index,
				item: items[index],
				style: `transform: translate3d(${translateX}%, 0, 0);`
			};
		});
	});

	let progressBarWidth = $derived(4 + progress * 18);
	let activeProgressIndex = $derived(isSliding ? targetIndex : currentIndex);

	function normalizeIndex(index: number): number {
		if (length === 0) {
			return 0;
		}

		return ((index % length) + length) % length;
	}

	function startSlide(direction: number) {
		if (length < 2 || isSliding === true) {
			return;
		}

		targetIndex = normalizeIndex(currentIndex + direction);
		progress = 0;
		isSliding = true;
		transitionsEnabled = true;
		slideOffset = -direction;

		if (slideTimeout !== undefined) {
			clearTimeout(slideTimeout);
		}

		slideTimeout = setTimeout(() => {
			transitionsEnabled = false;
			currentIndex = targetIndex;
			slideOffset = 0;

			requestAnimationFrame(() => {
				transitionsEnabled = true;
				isSliding = false;
				startAutoAdvance();
			});
		}, slideDurationMs);
	}

	function goToPrevious() {
		stopAutoAdvance();
		startSlide(-1);
	}

	function goToNext() {
		stopAutoAdvance();
		startSlide(1);
	}

	function didTapLeft() {
		goToPrevious();
	}

	function didTapRight() {
		goToNext();
	}

	function tickAutoAdvance(timestamp: number) {
		if (autoAdvanceStartTime === undefined) {
			autoAdvanceStartTime = timestamp;
		}

		const elapsed = timestamp - autoAdvanceStartTime;

		progress = Math.min(elapsed / autoAdvanceDelayMs, 1);

		if (elapsed >= autoAdvanceDelayMs) {
			stopAutoAdvance();

			setTimeout(() => {
				startSlide(1);
			}, 0);

			return;
		}

		autoAdvanceAnimationFrame = requestAnimationFrame(tickAutoAdvance);
	}

	function startAutoAdvance() {
		if (autoAdvanceAnimationFrame !== undefined || isVisible === false) {
			return;
		}

		autoAdvanceStartTime = undefined;
		autoAdvanceAnimationFrame = requestAnimationFrame(tickAutoAdvance);
	}

	function stopAutoAdvance() {
		if (autoAdvanceAnimationFrame !== undefined) {
			cancelAnimationFrame(autoAdvanceAnimationFrame);
			autoAdvanceAnimationFrame = undefined;
		}

		autoAdvanceStartTime = undefined;
	}

	function didChangeVisibility(entries: IntersectionObserverEntry[]) {
		const entry = entries[0];

		isVisible = entry.isIntersecting;

		if (isVisible === true) {
			startAutoAdvance();
		} else {
			stopAutoAdvance();
		}
	}

	$effect(() => {
		if (container === undefined) {
			return;
		}

		visibilityObserver = new IntersectionObserver(didChangeVisibility, {
			threshold: 0
		});

		visibilityObserver.observe(container);

		return () => {
			if (visibilityObserver !== undefined) {
				visibilityObserver.disconnect();
			}
		};
	});

	onDestroy(() => {
		stopAutoAdvance();

		if (slideTimeout !== undefined) {
			clearTimeout(slideTimeout);
		}
	});
</script>

<div
	bind:this={container}
	class="border-cumulus relative aspect-[360/560] w-full overflow-hidden border-x-16">
	{#each visibleItems as entry (entry.key)}
		<div
			class="absolute inset-0 will-change-transform"
			class:transition-transform={transitionsEnabled}
			class:duration-400={transitionsEnabled}
			class:ease-out={transitionsEnabled}
			style={entry.style}>
			{#if entry.item.image !== undefined}
				<img
					src={entry.item.image}
					alt=""
					class="h-full w-full rounded-[2px] object-cover" />
			{:else}
				<div class="bg-driveway/20 h-full w-full rounded-[2px]"></div>
			{/if}
			<div
				class="bg-cumulus/20 absolute bottom-0 left-0 flex w-full flex-col rounded-[2px] p-4 py-2 font-medium backdrop-blur-lg">
				<span class="text-cumulus">{entry.item.year}</span>
				<span class="text-driveway">{entry.item.text}</span>
			</div>
		</div>
	{/each}

	<div
		class="bg-cumulus/20 absolute top-2 left-1/2 z-20 flex -translate-x-1/2 items-center gap-1 rounded-[2px] px-2 py-2 backdrop-blur-lg transition-opacity duration-300"
		class:opacity-0={!isVisible}
		class:opacity-100={isVisible}>
		{#each items as _, index}
			{@const isActiveItem = index === activeProgressIndex}
			{@const isCompletedItem = index < activeProgressIndex}

			<div
				class="bg-cumulus/60 relative h-1 w-[22px] overflow-hidden rounded-full">
				{#if isActiveItem}
					<div
						class="bg-driveway absolute top-0 left-0 h-full rounded-full"
						style:width="{progressBarWidth}px">
					</div>
				{:else if isCompletedItem}
					<div
						class="bg-driveway absolute top-0 left-0 h-full w-full rounded-full">
					</div>
				{/if}
			</div>
		{/each}
	</div>

	<button
		type="button"
		class="absolute top-0 left-0 z-10 h-full w-[30%] cursor-pointer bg-transparent"
		onclick={didTapLeft}
		aria-label="Previous"></button>

	<button
		type="button"
		class="absolute top-0 right-0 z-10 h-full w-[30%] cursor-pointer bg-transparent"
		onclick={didTapRight}
		aria-label="Next"></button>
</div>
