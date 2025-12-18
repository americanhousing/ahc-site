<script lang="ts">
	import { onDestroy, onMount } from "svelte";
	import TimelineMobile from "./TimelineMobile.svelte";

	type TimelineItem = {
		year: string;
		text: string;
		image?: string;
	};

	type Props = {
		items: TimelineItem[];
	};

	const { items }: Props = $props();
	const dragClickThresholdPx = 12;
	const dragMultiplier = 2;

	let scroller = $state<HTMLElement | undefined>(undefined);
	let horizontalPadding = $state<number>(0);
	let currentIndex = $state<number>(0);
	let windowWidth = $state<number>(
		typeof window !== "undefined" ? window.innerWidth : 1440
	);
	let isDragging = $state<boolean>(false);
	let dragPointerId = $state<number | null>(null);
	let dragStartX = $state<number>(0);
	let dragStartScrollLeft = $state<number>(0);
	let dragHasMoved = $state<boolean>(false);
	let dragResetTimeout: ReturnType<typeof setTimeout> | undefined = undefined;
	let dragCaptureTarget = $state<HTMLElement | null>(null);

	type DragSample = { x: number; time: number };

	let dragSamples: DragSample[] = [];
	const dragSampleLimit = 5;
	const velocityDecayFactor = 0.06;

	let itemDimensions = $derived.by(() => {
		const scaledWidth = (windowWidth * 1116) / 1440;
		const width = Math.min(1116, scaledWidth);
		const height = (width * 664) / 1116;

		return { width, height };
	});

	let scrollerStyle = $derived(
		`padding-left: ${horizontalPadding}px; padding-right: ${horizontalPadding}px;`
	);

	let itemStyle = $derived(
		`width: ${itemDimensions.width}px; height: ${itemDimensions.height}px; min-width: ${itemDimensions.width}px;`
	);

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
		if (isDragging || dragHasMoved) {
			return;
		}

		scrollToItem(index);
	}

	function calculateDragVelocity(): number {
		if (dragSamples.length < 2) {
			return 0;
		}

		const recentSamples = dragSamples.slice(-3);
		const first = recentSamples[0];
		const last = recentSamples[recentSamples.length - 1];
		const timeDelta = last.time - first.time;

		if (timeDelta === 0) {
			return 0;
		}

		const positionDelta = last.x - first.x;

		return (positionDelta / timeDelta) * 1000;
	}

	function snapToNearestItem(velocity: number = 0) {
		if (scroller === undefined) {
			return;
		}

		const itemElements = scroller.children;

		if (itemElements.length === 0) {
			return;
		}

		const projectedScrollDelta =
			velocity * velocityDecayFactor * dragMultiplier * -1;
		const projectedScrollLeft = scroller.scrollLeft + projectedScrollDelta;
		const projectedCenter = projectedScrollLeft + scroller.clientWidth / 2;

		let nearestIndex = 0;
		let smallestDistance = Number.POSITIVE_INFINITY;

		for (let index = 0; index < itemElements.length; index += 1) {
			const item = itemElements[index] as HTMLElement;
			const itemCenter = item.offsetLeft + item.offsetWidth / 2;
			const distance = Math.abs(itemCenter - projectedCenter);

			if (distance < smallestDistance) {
				smallestDistance = distance;
				nearestIndex = index;
			}
		}

		scrollToItem(nearestIndex);
	}

	function didStartDrag(event: PointerEvent) {
		if (scroller === undefined || event.button !== 0) {
			return;
		}

		const handle = (
			event.target as HTMLElement | null
		)?.closest<HTMLElement>("[data-timeline-handle]");
		const captureTarget = handle ?? scroller;

		dragPointerId = event.pointerId;
		isDragging = true;
		dragHasMoved = false;
		dragStartX = event.clientX;
		dragStartScrollLeft = scroller.scrollLeft;
		dragCaptureTarget = captureTarget;
		dragSamples = [{ x: event.clientX, time: performance.now() }];

		if (dragResetTimeout !== undefined) {
			clearTimeout(dragResetTimeout);
		}

		captureTarget?.setPointerCapture?.(event.pointerId);
	}

	function didDrag(event: PointerEvent) {
		if (
			isDragging === false ||
			dragPointerId !== event.pointerId ||
			scroller === undefined
		) {
			return;
		}

		const deltaX = event.clientX - dragStartX;

		if (Math.abs(deltaX) >= dragClickThresholdPx) {
			dragHasMoved = true;
		}

		dragSamples.push({ x: event.clientX, time: performance.now() });

		if (dragSamples.length > dragSampleLimit) {
			dragSamples.shift();
		}

		scroller.scrollLeft = dragStartScrollLeft - deltaX * dragMultiplier;
		event.preventDefault();
	}

	function didEndDrag(event: PointerEvent) {
		if (isDragging === false || dragPointerId !== event.pointerId) {
			return;
		}

		const movedDuringDrag = dragHasMoved;

		if (dragCaptureTarget?.hasPointerCapture?.(event.pointerId)) {
			dragCaptureTarget.releasePointerCapture(event.pointerId);
		}

		isDragging = false;
		dragPointerId = null;
		dragCaptureTarget = null;

		if (dragResetTimeout !== undefined) {
			clearTimeout(dragResetTimeout);
		}

		dragResetTimeout = window.setTimeout(() => {
			dragHasMoved = false;
		}, 0);

		if (movedDuringDrag === true) {
			const velocity = calculateDragVelocity();

			snapToNearestItem(velocity);
		}
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
		windowWidth = window.innerWidth;
		calculatePadding();
	}

	onMount(() => {
		calculatePadding();
	});

	onDestroy(() => {
		if (dragResetTimeout !== undefined) {
			clearTimeout(dragResetTimeout);
		}
	});
</script>

<svelte:window onresize={didResizeWindow} onkeydown={didPressKey} />

<div class="hidden md:block">
	<div
		bind:this={scroller}
		class="scrollbar-none flex cursor-grab flex-nowrap gap-6 overflow-x-auto"
		class:cursor-grabbing={isDragging}
		style:touch-action="pan-y"
		style={scrollerStyle}
		onpointerdown={didStartDrag}
		onpointermove={didDrag}
		onpointerup={didEndDrag}
		onpointercancel={didEndDrag}>
		{#each items as item, index}
			<button
				type="button"
				onclick={() => didClickItem(index)}
				class="bg-driveway/20 relative cursor-pointer rounded-[2px]"
				style={itemStyle}
				data-timeline-handle>
				{#if item.image !== undefined}
					<img
						src={item.image}
						alt=""
						class="h-full w-full rounded-[2px] object-cover" />
				{/if}
				<div
					class="bg-cumulus/20 font-die-a type-title absolute bottom-6 left-6 flex w-auto gap-2 rounded-[2px] px-6 py-4 font-medium backdrop-blur-lg">
					<span class="text-cumulus">{item.year}</span>
					<span class="text-driveway">{item.text}</span>
				</div>
			</button>
		{/each}
	</div>
</div>

<div class="md:hidden">
	<TimelineMobile {items} />
</div>
