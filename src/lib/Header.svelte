<script lang="ts">
	import Logo from "./Logo.svelte";
	import Marquee from "./Marquee.svelte";
</script>

<div class="fixed top-0 z-10 w-screen">
	<div class="bg-cumulus/20 backdrop-blur-lg">
		<Marquee items={["$6b raised in series A"]} />
	</div>
	<div class="relative mx-auto w-full max-w-[1440px]">
		<Logo />
		<div
			class="absolute top-4 right-4 flex h-[50px] items-center md:top-6 md:right-6">
			<a
				href="/careers"
				class="bg-cumulus text-driveway flex gap-2 rounded-full px-4 py-2 text-[18px] leading-[24px]">
				Careers
				<img
					src="/icons/arrow-right-driveway.svg"
					width="12"
					height="10"
					alt=">" />
			</a>
		</div>
	</div>
</div>
