<script lang="ts">
	import { onDestroy, onMount } from "svelte";

	type Props = {
		images: string[];
		marginSize: number;
		gap: number;
	};

	const { images, marginSize = 0.1, gap = 24 }: Props = $props();

	const visibleOffsets = [-2, -1, 0, 1, 2];
	const slideDurationMs = 400;

	let container = $state<HTMLElement | undefined>(undefined);

	let windowSize = $state<{ width: number; height: number }>({
		width: window.innerWidth,
		height: window.innerHeight
	});

	let indexForCurrentImage = $state<number>(0);
	let slideOffset = $state<number>(0);
	let isSliding = $state<boolean>(false);
	let transitionsEnabled = $state<boolean>(true);
	let slideTimeout: ReturnType<typeof setTimeout> | undefined = undefined;

	let baseImageDimensions = $derived.by(() => {
		const scaledWidth = (windowSize.width * 1116) / 1440;
		const maxWidth = windowSize.width * (1 - marginSize * 2);
		const availableWidth = Math.max(maxWidth, 1);
		const width = Math.min(1116, scaledWidth, availableWidth);
		const height = (width * 664) / 1116;

		return { width, height };
	});

	let styleForContainer = $derived.by(() => {
		const { height } = baseImageDimensions;

		return `height: ${height}px`;
	});

	let length = $derived.by(() => images.length);

	let visibleItems = $derived.by(() => {
		if (length === 0) {
			return [];
		}

		return visibleOffsets.map((offset) => {
			const index = normalizeIndex(indexForCurrentImage + offset);

			return {
				key: `${index}-${offset}`,
				offset,
				index,
				image: images.at(index)
			};
		});
	});

	let stylesForSlots = $derived.by(() => {
		const { width, height } = baseImageDimensions;
		const centerX = (windowSize.width - width) * 0.5;

		return visibleItems.map((item) => {
			const effectiveOffset = item.offset + slideOffset;
			const translateX = centerX + effectiveOffset * (width + gap);

			const distance = Math.min(Math.abs(effectiveOffset), 1);
			const scale = 1 - distance * 0.15;

			let origin = "center";

			if (effectiveOffset < 0) {
				origin = "center right";
			} else if (effectiveOffset > 0) {
				origin = "center left";
			}

			return {
				container: `width: ${width}px; height: ${height}px; transform: translate3d(${translateX}px, 0, 0);`,
				image: `width: ${width}px; height: ${height}px; transform-origin: ${origin}; transform: scale(${scale});`
			};
		});
	});

	function normalizeIndex(index: number) {
		if (length === 0) {
			return 0;
		}

		return ((index % length) + length) % length;
	}

	function isVisible() {
		if (container === undefined) {
			return false;
		}

		const rect = container.getBoundingClientRect();

		return rect.bottom > 0 && rect.top < window.innerHeight;
	}

	function didResizeViewport() {
		windowSize = {
			width: window.innerWidth,
			height: window.innerHeight
		};
	}

	function goToPreviousImage() {
		startSlide(-1);
	}

	function goToNextImage() {
		startSlide(1);
	}

	function didClickItem(offset: number) {
		if (offset === 0) {
			return;
		}

		const direction = offset < 0 ? -1 : 1;

		startSlide(direction);
	}

	function startSlide(direction: number) {
		if (length < 2 || isSliding) {
			return;
		}

		const targetIndex = normalizeIndex(indexForCurrentImage + direction);

		isSliding = true;
		transitionsEnabled = true;
		slideOffset = -direction;

		if (slideTimeout !== undefined) {
			clearTimeout(slideTimeout);
		}

		slideTimeout = window.setTimeout(() => {
			transitionsEnabled = false;
			indexForCurrentImage = targetIndex;
			slideOffset = 0;

			requestAnimationFrame(() => {
				transitionsEnabled = true;
				isSliding = false;
			});
		}, slideDurationMs);
	}

	function didPressKey(e: KeyboardEvent) {
		switch (e.key) {
			case "ArrowLeft": {
				if (isVisible() === false) {
					return;
				}

				goToPreviousImage();

				break;
			}

			case "ArrowRight": {
				if (isVisible() === false) {
					return;
				}

				goToNextImage();

				break;
			}

			default:
				break;
		}
	}

	onMount(() => {
		didResizeViewport();
	});

	onDestroy(() => {
		if (slideTimeout !== undefined) {
			clearTimeout(slideTimeout);
		}
	});
</script>

<svelte:window onresize={didResizeViewport} onkeyup={didPressKey} />

<div class="flex flex-col gap-4 px-4 md:hidden">
	{#each images as image, index}
		<img
			class="bg-driveway/20 h-auto w-full rounded-[2px] object-cover"
			src={""}
			width="358"
			height="213"
			alt="" />
	{/each}
</div>

<div
	class="relative hidden w-screen overflow-hidden md:block"
	style={styleForContainer}
	bind:this={container}>
	{#each visibleItems as item, slotIndex (item.key)}
		{#if item.offset !== 0}
			<button
				class="absolute top-0 left-0 cursor-pointer border-none bg-transparent p-0 transition-transform duration-400 ease-out will-change-transform"
				class:transition-none={!transitionsEnabled}
				style={stylesForSlots[slotIndex]?.container}
				onclick={() => didClickItem(item.offset)}>
				<img
					class="bg-driveway/20 cursor-pointer rounded-[2px] object-cover transition-transform duration-400 ease-out"
					src={""}
					width="100%"
					height="100%"
					alt=""
					style={stylesForSlots[slotIndex]?.image} />
			</button>
		{:else}
			<div
				class="absolute top-0 left-0 transition-transform duration-400 ease-out will-change-transform"
				class:transition-none={!transitionsEnabled}
				style={stylesForSlots[slotIndex]?.container}>
				<img
					class="bg-driveway/20 rounded-[2px] object-cover transition-transform duration-400 ease-out"
					src={""}
					width="100%"
					height="100%"
					alt=""
					style={stylesForSlots[slotIndex]?.image} />
			</div>
		{/if}
	{/each}
	<div
		class="bg-cumulus/60 absolute bottom-6 left-1/2 z-100 flex -translate-x-1/2 items-center justify-center rounded-[2px] backdrop-blur-lg">
		<button
			class="cursor-pointer px-6 py-5 pr-2"
			onclick={goToPreviousImage}>
			<img
				class="-scale-x-100"
				src="/icons/arrow-right-driveway.svg"
				width="12"
				height="10"
				alt="←" />
		</button>
		<button class="cursor-pointer px-6 py-5 pl-2" onclick={goToNextImage}>
			<img
				src="/icons/arrow-right-driveway.svg"
				width="12"
				height="10"
				alt="→" />
		</button>
	</div>
</div>
