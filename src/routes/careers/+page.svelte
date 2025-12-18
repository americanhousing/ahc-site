<script>
	import Footer from "$lib/Footer.svelte";
	import Header from "$lib/Header.svelte";
	import Rollover from "$lib/Rollover.svelte";
</script>

<Header />

<main>
	<div class="bg-cumulus">
		<div class="h-[110px] md:h-[120px]"></div>
		<div
			class="mx-auto flex min-h-[40vh] max-w-[1440px] flex-col px-4 md:flex-row md:px-6">
			<h4
				class="font-die-d text-driveway type-display font-medium md:hidden">
				Careers
			</h4>
			<div class="h-[24px] md:hidden"></div>
			<div
				class="bg-driveway/20 mr-6 aspect-[560/800] h-auto w-full flex-5/12 rounded-[2px] lg:aspect-[556/800]">
			</div>
			<div
				class="md:border-l-driveway flex flex-7/12 flex-col md:border-l-1 md:pl-6">
				<h4
					class="font-die-d text-driveway type-display hidden font-medium md:block">
					Careers
				</h4>
				<div class="min-h-[160px] flex-1 md:min-h-[200px]"></div>
				{#each Array(3).fill(undefined) as _}
					<div class="border-driveway flex border-b-1 py-4 md:py-6">
						<div class="font-die-a type-body flex flex-col">
							<div>Title</div>
							<div class="text-driveway/60">Austin, TX</div>
						</div>
						<div class="flex-1"></div>
						<a
							class="text-blue font-die-a type-body group flex items-center gap-2 font-normal"
							href="/careers">
							<Rollover text="Apply" />
							<img
								src="/icons/arrow-right-blue.svg"
								width="12"
								height="10"
								alt="→" />
						</a>
					</div>
				{/each}
			</div>
		</div>
		<div class="h-[160px] md:h-[240px]"></div>
	</div>
	<Footer />
</main>
