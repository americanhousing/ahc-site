<script lang="ts">
	import { onMount, onDestroy } from "svelte";

	interface Props {
		variant?: "default" | "inverted";
	}

	let { variant = "default" }: Props = $props();

	let isInverted = $derived(variant === "inverted");

	let thresholdElement = $state<HTMLElement | undefined>();
	let shouldElevateRoof = $state<boolean>(false);
	let shouldElevateTopFloor = $state<boolean>(false);
	let shouldElevateBottomFloor = $state<boolean>(false);
	let isRoofRevealed = $state<boolean>(false);
	let isBottomRevealed = $state<boolean>(false);

	function updateElevationState() {
		if (thresholdElement === undefined) {
			return;
		}

		const rect = thresholdElement.getBoundingClientRect();

		shouldElevateRoof =
			isRoofRevealed === true || rect.top < window.innerHeight * 0.8;

		shouldElevateTopFloor =
			isBottomRevealed === true ||
			rect.bottom <= window.innerHeight * 1.1;

		shouldElevateBottomFloor =
			isBottomRevealed === true ||
			rect.bottom <= window.innerHeight * 1.1;

		isRoofRevealed = isRoofRevealed || shouldElevateRoof;

		isBottomRevealed =
			isBottomRevealed ||
			shouldElevateTopFloor ||
			shouldElevateBottomFloor;
	}

	function didChangeViewport() {
		updateElevationState();
	}

	onMount(() => {
		updateElevationState();
	});

	onDestroy(() => {
		document.body.style.backgroundColor = "";
	});
</script>

<svelte:window onscroll={didChangeViewport} onresize={didChangeViewport} />

<div class={isInverted === true ? "bg-cumulus" : "bg-blue"}>
	<div
		class="font-die-a type-caption mx-auto flex h-[890px] max-h-[110svh] min-h-[400px] max-w-[1440px] flex-col overflow-hidden p-6 md:h-[70vh] md:max-h-[800px] md:min-h-[400px] {isInverted ===
		true
			? 'text-blue'
			: 'text-cumulus'}"
		bind:this={thresholdElement}>
		<div class="h-[80px] md:hidden"></div>
		<img
			class="hidden w-full translate-y-24 opacity-0 transition-all ease-out md:block md:duration-1500"
			class:translate-none={shouldElevateRoof}
			class:opacity-100={shouldElevateRoof}
			src={isInverted === true
				? "/images/american-housing-blue.svg"
				: "/images/american-housing.svg"}
			width="1385"
			height="180"
			alt="American Housing" />
		<img
			class="w-full translate-y-1/3 opacity-0 transition-all duration-1500 ease-out md:hidden"
			class:translate-none={shouldElevateRoof}
			class:opacity-100={shouldElevateRoof}
			src={isInverted === true
				? "/images/american-housing-alt-blue.svg"
				: "/images/american-housing-alt.svg"}
			width="355"
			height="172"
			alt="American Housing" />
		<div class="flex-1"></div>
		<div
			class="flex translate-y-12 flex-row-reverse items-start gap-0 opacity-0 transition-all delay-200 duration-1500 ease-out md:flex-row md:gap-12"
			class:opacity-100={shouldElevateTopFloor}
			class:translate-none={shouldElevateTopFloor}>
			<div class="flex items-center gap-6">
				<img
					src={isInverted === true
						? "/icons/social-linkedin-blue.svg"
						: "/icons/social-linkedin.svg"}
					width="18"
					height="18"
					alt="Linkedin" />
				<img
					src={isInverted === true
						? "/icons/social-x-blue.svg"
						: "/icons/social-x.svg"}
					width="20"
					height="18"
					alt="X" />
				<img
					src={isInverted === true
						? "/icons/social-instagram-blue.svg"
						: "/icons/social-instagram.svg"}
					width="18"
					height="18"
					alt="Instagram" />
			</div>
			<div class="flex-1"></div>
			<div
				class="font-die-a type-caption flex flex-col gap-6 md:flex-row md:gap-12 {isInverted ===
				true
					? 'text-blue'
					: 'text-cumulus'}">
				<a href="/">Contact</a>
				<a href="/mission">Mission</a>
				<a href="/faq">FAQs</a>
				<a href="/">Research</a>
			</div>
			<div
				class="hidden w-[250px] border-b-1 pb-0.5 md:flex {isInverted ===
				true
					? 'border-b-blue'
					: 'border-b-cumulus'}">
				<input
					class="relative -top-[1.5px] flex-1 appearance-none text-inherit outline-none"
					placeholder="Enter Email"
					type="text" />
				<input
					class="relative -top-[1px] appearance-none"
					type="submit"
					value="Sign up" />
			</div>
		</div>
		<div class="h-[24px] md:hidden"></div>
		<div
			class="flex translate-y-12 border-b-1 pb-0.5 opacity-0 transition-all delay-400 duration-1500 ease-out md:hidden md:w-[250px] {isInverted ===
			true
				? 'border-b-blue'
				: 'border-b-cumulus'}"
			class:opacity-100={shouldElevateBottomFloor}
			class:translate-none={shouldElevateBottomFloor}>
			<input
				class="relative -top-[1.5px] flex-1 appearance-none text-inherit outline-none"
				placeholder="Enter Email"
				type="text" />
			<input
				class="relative -top-[1px] appearance-none"
				type="submit"
				value="Sign up" />
		</div>
		<div class="h-[40px] md:h-[64px]"></div>
		<div
			class="flex translate-y-12 flex-col-reverse font-medium opacity-0 transition-all delay-600 duration-1500 ease-out md:flex-row md:font-normal"
			class:opacity-100={shouldElevateBottomFloor}
			class:translate-none={shouldElevateBottomFloor}>
			<div>
				© The American Housing Corporation, 2025<br />
				4422 Supply Ct Road, Austin, TX 78744 USA
			</div>
			<div class="min-h-[40px] flex-1 md:h-0 md:min-h-[48px]"></div>
			<div class="flex items-center gap-6">
				<img
					src={isInverted === true
						? "/images/flag-blue.svg"
						: "/images/flag-cumulus.svg"}
					width="52"
					height="30"
					alt="" />
				<span>Always made<br />in the USA</span>
			</div>
		</div>
	</div>
</div>
