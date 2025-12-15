<script lang="ts">
	import { onMount } from "svelte";

	type Item = {
		title: string;
		text: string;
	};

	type Props = {
		items: Item[];
		color?: "blue" | "driveway";
	};

	const { items, color = "blue" }: Props = $props();
	const EXTRA_HEIGHT_PADDING_PX = 3;

	let indexForActiveItem = $state<number>(0);
	let measuredHeights = $state<Record<number, number>>({});
	const contentNodes = new Map<number, HTMLElement>();

	function didClickItem(index: number) {
		indexForActiveItem = index;
	}

	function measureHeightForIndex(index: number) {
		const node = contentNodes.get(index);

		if (node === undefined) {
			return;
		}

		const heightWithPadding = node.scrollHeight + EXTRA_HEIGHT_PADDING_PX;

		measuredHeights = { ...measuredHeights, [index]: heightWithPadding };
	}

	function measureAllHeights() {
		contentNodes.forEach((_, index) => measureHeightForIndex(index));
	}

	function measureContentHeight(node: HTMLElement, index: number) {
		contentNodes.set(index, node);

		const measure = () => measureHeightForIndex(index);
		const observer = new ResizeObserver(() => measure());

		observer.observe(node);
		measure();

		return {
			destroy() {
				observer.disconnect();
				contentNodes.delete(index);
			}
		};
	}

	function heightForItem(index: number, isActive: boolean) {
		if (isActive === false) {
			return "0px";
		}

		const measuredHeight = measuredHeights[index];

		return measuredHeight === undefined ? "auto" : `${measuredHeight}px`;
	}

	onMount(() => {
		const handleResize = () => measureAllHeights();

		window.addEventListener("resize", handleResize);
		measureAllHeights();

		return () => {
			window.removeEventListener("resize", handleResize);
		};
	});
</script>

<div class="font-die-a type-title flex flex-col gap-6 font-medium">
	{#each items as item, index}
		{@const isActive = index === indexForActiveItem}

		<div class="border-b-driveway group border-b-1 pb-6">
			<button
				class="flex w-full cursor-pointer items-center gap-2 text-left"
				onclick={() => didClickItem(index)}>
				<div class="relative h-[16px] w-[16px]">
					<img
						class="absolute top-0 left-0 group-hover:opacity-100"
						class:opacity-0={isActive === false}
						src="/icons/bullet-active-{color}.svg"
						width="16"
						height="16"
						alt="" />
					<img
						class="absolute top-0 left-0"
						class:opacity-0={isActive === true}
						src="/icons/bullet-inactive-{color}.svg"
						width="16"
						height="16"
						alt="" />
				</div>
				{item.title}
			</button>

			<div
				class="overflow-hidden transition-[height] duration-500 ease-in-out"
				style={`height: ${heightForItem(index, isActive)}`}>
				<div use:measureContentHeight={index}>
					<div class="h-[24px] md:h-[32px] xl:h-[40px]"></div>
					<div
						class="text-driveway font-normal transition-opacity duration-250 ease-in-out"
						class:opacity-0={!isActive}
						class:opacity-100={isActive}
						class:delay-350={isActive}
						class:delay-0={!isActive}>
						{item.text}
					</div>
				</div>
			</div>
		</div>
	{/each}
</div>
