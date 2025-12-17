<script lang="ts">
	import { goto } from "$app/navigation";
	import { page } from "$app/stores";

	interface Props {
		isOnLightBackground: boolean;
	}

	let { isOnLightBackground }: Props = $props();

	const isHomePage = $derived($page.url.pathname === "/");

	function didClickLogo() {
		if (isHomePage === true) {
			window.scrollTo({ top: 0, behavior: "smooth" });
		} else {
			goto("/");
		}
	}
</script>

<button
	onclick={didClickLogo}
	class="absolute top-4 left-4 cursor-pointer md:top-6 md:left-6">
	<img
		class="absolute top-0 left-0 transition-opacity duration-500"
		class:opacity-0={isOnLightBackground === false}
		src="/images/logo-color.svg"
		width="100"
		height="50"
		alt="The American Housing Corporation" />
	<img
		class="transition-opacity duration-500"
		class:opacity-0={isOnLightBackground === true}
		src="/images/logo-cumulus.svg"
		width="100"
		height="50"
		alt="The American Housing Corporation" />
</button>
