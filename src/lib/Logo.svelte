<script lang="ts">
	import { onMount } from "svelte";

	let isOnLightBackground = $state(false);
	let logoElement: HTMLButtonElement;

	function didClickLogo() {
		window.scrollTo({ top: 0, behavior: "smooth" });
	}

	function checkBackground() {
		if (logoElement === undefined) {
			return;
		}

		const logoRect = logoElement.getBoundingClientRect();
		const logoCenter = logoRect.top + logoRect.height / 2;
		const sections = document.querySelectorAll("main > div[class*='bg-']");

		for (const section of sections) {
			const sectionRect = section.getBoundingClientRect();
			const isOverlapping =
				logoCenter >= sectionRect.top &&
				logoCenter <= sectionRect.bottom;

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

<button
	bind:this={logoElement}
	onclick={didClickLogo}
	class="absolute top-6 left-6 cursor-pointer">
	<img
		class="absolute top-0 left-0 transition-opacity duration-300"
		class:opacity-0={isOnLightBackground === false}
		src="/images/logo-color.svg"
		width="100"
		height="50"
		alt="The American Housing Corporation" />
	<img
		class="transition-opacity duration-300"
		class:opacity-0={isOnLightBackground === true}
		src="/images/logo-cumulus.svg"
		width="100"
		height="50"
		alt="The American Housing Corporation" />
</button>
