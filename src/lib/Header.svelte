<script lang="ts">
	import { onMount } from "svelte";
	import Logo from "./Logo.svelte";

	let isOnLightBackground = $state(false);
	let headerElement: HTMLDivElement;

	function checkBackground() {
		if (headerElement === undefined) {
			return;
		}

		const headerRect = headerElement.getBoundingClientRect();
		const headerCenter = headerRect.top + headerRect.height / 2;
		const sections = document.querySelectorAll("main > div[class*='bg-']");

		for (const section of sections) {
			const sectionRect = section.getBoundingClientRect();
			const isOverlapping =
				headerCenter >= sectionRect.top &&
				headerCenter <= sectionRect.bottom;

			if (isOverlapping === false) {
				continue;
			}

			isOnLightBackground = section.classList.contains("bg-cumulus");
			return;
		}
	}

	onMount(() => {
		checkBackground();
		window.addEventListener("scroll", checkBackground);
		window.addEventListener("resize", checkBackground);

		return () => {
			window.removeEventListener("scroll", checkBackground);
			window.removeEventListener("resize", checkBackground);
		};
	});
</script>

<div bind:this={headerElement} class="sticky -top-13 z-10 h-0 w-screen">
	<div class="relative top-13 mx-auto w-full max-w-[1440px]">
		<Logo {isOnLightBackground} />
		<div
			class="absolute top-4 right-4 flex h-[50px] items-center md:top-6 md:right-6">
			<a
				href="/careers"
				class="flex gap-2 rounded-full px-4 py-2 text-[18px] leading-[24px] transition-all duration-150"
				class:bg-cumulus={isOnLightBackground === false}
				class:text-driveway={isOnLightBackground === false}
				class:bg-driveway={isOnLightBackground === true}
				class:text-cumulus={isOnLightBackground === true}>
				Careers
				<img
					class:hidden={isOnLightBackground === true}
					src="/icons/arrow-right-driveway.svg"
					width="12"
					height="10"
					alt=">" />
				<img
					class:hidden={isOnLightBackground === false}
					src="/icons/arrow-right-cumulus.svg"
					width="12"
					height="10"
					alt=">" />
			</a>
		</div>
	</div>
</div>
