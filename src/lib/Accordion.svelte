<script lang="ts">
	type Item = {
		title: string;
		text: string;
	};

	type Props = {
		items: Item[];
	};

	const { items }: Props = $props();

	let indexForActiveItem = $state<number>(0);

	function didClickItem(index: number) {
		indexForActiveItem = index;
	}
</script>

<div
	class="font-die-a flex flex-col gap-6 text-[24px] leading-[24px] font-medium">
	{#each items as item, index}
		{@const isActive = index === indexForActiveItem}

		<div class="border-b-driveway border-b-1 pb-6">
			<button
				class="flex w-full cursor-pointer items-center gap-2 text-left"
				onclick={() => didClickItem(index)}>
				<div class="relative h-[16px] w-[16px]">
					<img
						class="absolute top-0 left-0"
						class:opacity-0={isActive === false}
						src="/icons/bullet-active-blue.svg"
						width="16"
						height="16"
						alt="" />
					<img
						class="absolute top-0 left-0"
						class:opacity-0={isActive === true}
						src="/icons/bullet-inactive-blue.svg"
						width="16"
						height="16"
						alt="" />
				</div>
				{item.title}
			</button>

			{#if isActive === true}
				<div>
					<div class="h-[40px]"></div>
					<div class="text-driveway font-normal">
						{item.text}
					</div>
				</div>
			{/if}
		</div>
	{/each}
</div>
