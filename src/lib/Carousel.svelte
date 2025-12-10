<script lang="ts">
	import { onMount } from "svelte";

	type Props = {
		images: string[];
		marginSize: number;
		gap: number;
	};

	const { images, marginSize = 0.1, gap = 24 }: Props = $props();

	let container = $state<HTMLElement | undefined>(undefined);

	let windowSize = $state<{ width: number; height: number }>({
		width: window.innerWidth,
		height: window.innerHeight
	});

	let indexForCurrentImage = $state<number>(2);

	let baseImageDimensions = $derived.by(() => {
		const width = Math.min(1116, (windowSize.width * 1116) / 1440);
		const height = (width * 664) / 1116;

		return { width, height };
	});

	let styleForContainer = $derived.by(() => {
		const { height } = baseImageDimensions;

		return `height: ${height}px`;
	});

	let styleForImageContainers = $derived.by(() => {
		const { width, height } = baseImageDimensions;

		return images.map((_, index) => {
			let x = 0.0;

			if (index === indexForImageAt(0)) {
				x = (window.innerWidth - width) * 0.5;
			} else if (index === indexForImageAt(-1)) {
				x = (window.innerWidth - width) * 0.5 - width - gap;
			} else if (index === indexForImageAt(1)) {
				x = (window.innerWidth - width) * 0.5 + width + gap;
			}

			return (
				`width: ${width}px; height: ${height}px;` +
				`transform: translate3d(${x}px, 0, 0)`
			);
		});
	});

	let styleForImages = $derived.by(() => {
		const { width, height } = baseImageDimensions;

		return images.map((_, index) => {
			let scale = 1.0;

			if (index !== indexForImageAt(0)) {
				scale = 0.85;
			}

			let origin = "";

			if (index === indexForImageAt(-1)) {
				origin = "center right";
			} else if (index === indexForImageAt(1)) {
				origin = "center left";
			}

			return (
				`width: ${width}px; height: ${height}px;` +
				`transform-origin: ${origin}; transform: scale(${scale});`
			);
		});
	});

	function indexForImageAt(offset: number) {
		const length = images.length;

		const normalIndex =
			(((indexForCurrentImage + offset) % length) + length) % length;

		const image = images.at(normalIndex);

		if (image === undefined) {
			return -1;
		}

		return images.indexOf(image);
	}

	function isVisible() {
		if (container === undefined) {
			return false;
		}

		const rect = container.getBoundingClientRect();

		return true;
	}

	function didResizeViewport() {
		windowSize = {
			width: window.innerWidth,
			height: window.innerHeight
		};
	}

	function didPressKey(e: KeyboardEvent) {
		switch (e.key) {
			case "ArrowLeft": {
				if (isVisible() === false) {
					return;
				}

				// indexForCurrentImage -= 1;

				break;
			}

			case "ArrowRight": {
				if (isVisible() === false) {
					return;
				}

				// indexForCurrentImage += 1;

				break;
			}

			default:
				break;
		}
	}

	onMount(() => {
		didResizeViewport();
	});
</script>

<svelte:window onresize={didResizeViewport} onkeyup={didPressKey} />

<div
	class="relative w-screen overflow-hidden"
	style={styleForContainer}
	bind:this={container}>
	{#each images as image, index}
		<div
			class="absolute top-0 left-0 transition-all duration-1000"
			style={styleForImageContainers[index]}>
			<img
				class="bg-driveway rounded-[2px] object-cover transition-all duration-1000"
				src={""}
				width="100%"
				height="100%"
				alt=""
				style={styleForImages[index]} />
		</div>
	{/each}
	<div
		class="bg-cumulus/60 absolute bottom-6 left-1/2 z-100 flex -translate-x-1/2 items-center justify-center rounded-[2px] backdrop-blur-lg">
		<button class="px-6 py-5 pr-2">
			<img
				class="-scale-x-100"
				src="/icons/arrow-right-driveway.svg"
				width="12"
				height="10"
				alt="←" />
		</button>
		<button class="px-6 py-5 pl-2">
			<img
				src="/icons/arrow-right-driveway.svg"
				width="12"
				height="10"
				alt="→" />
		</button>
	</div>
</div>
