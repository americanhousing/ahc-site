<script lang="ts">
	import { Accordion, Carousel, Footer, Header, Timeline } from "$lib";
	import Marquee from "$lib/Marquee.svelte";
	import Rollover from "$lib/Rollover.svelte";
	import { onMount } from "svelte";

	let shouldDisplayShiftedStage = $state<boolean>(false);

	function updateHeadingAnimation() {
		shouldDisplayShiftedStage = window.scrollY > window.innerHeight * 0.5;
	}

	function didChangeViewport() {
		updateHeadingAnimation();
	}

	onMount(() => {
		updateHeadingAnimation();
	});
</script>

<svelte:window onscroll={didChangeViewport} onresize={didChangeViewport} />

<Header />

<main>
	<div class="bg-driveway relative">
		<div class="bg-cumulus/20 absolute backdrop-blur-lg">
			<Marquee items={["$6b raised in series A"]} />
		</div>
		<div class="mx-auto flex h-svh max-w-[1440px] items-end p-4 md:p-6">
			<h1
				class="font-die-d text-cumulus type-display font-medium transition-[color,transform] duration-500 will-change-transform"
				class:shifted-alpha={shouldDisplayShiftedStage}>
				Saving the<br />
				American Dream
			</h1>
		</div>
	</div>

	<div class="bg-cumulus mx-auto max-w-[1440px]">
		<div class="h-4 md:h-6"></div>
		<div class="flex flex-col gap-4 px-4 md:flex-row md:gap-6 md:px-6">
			<div
				class="flex-1/2 transition-[color,transform] duration-500 will-change-transform"
				class:shifted-beta={shouldDisplayShiftedStage}>
				<h2 class="font-die-d text-driveway type-display font-medium">
					Through All-Out<br />
					Housing Production
				</h2>
				<div class="h-[48px]"></div>
				<div class="sticky top-4 mb-23">
					<div
						class="text-driveway font-die-a type-title font-medium">
						We’re building an abundance of beautiful starter homes
						across the United States, in cities where families love
						to live.
					</div>
					<div class="h-[48px] md:h-[64px]"></div>
					<a
						class="text-blue font-die-a type-body group flex items-center gap-2 self-start font-normal"
						href="/mission">
						<Rollover text="Our Mission" />
						<img
							src="/icons/arrow-right-blue.svg"
							width="12"
							height="10"
							alt="→" />
					</a>
				</div>
			</div>
			<div
				class="bg-driveway/20 aspect-[476/552] flex-1/2 rounded-[2px] lg:aspect-[684/800]">
			</div>
		</div>
	</div>

	<div class="bg-cumulus">
		<div class="h-[160px] md:h-[240px]"></div>
		<div class="mx-auto max-w-[1440px] px-4 md:px-6">
			<h3 class="text-driveway font-die-d type-display font-medium">
				Beautiful, Adaptable Design
			</h3>
		</div>
		<div class="h-4 md:h-[40px]"></div>
		<Carousel
			images={[
				{
					src: "https://picsum.photos/1440/1000",
					caption: "Caption for image one"
				},
				{
					src: "https://picsum.photos/1440/1200",
					caption: "Caption for image two"
				},
				{
					src: "https://picsum.photos/1440/1300",
					caption: "Caption for image three"
				}
			]}
			marginSize={0.1}
			gap={24} />
	</div>

	<div class="bg-cumulus">
		<div class="h-[160px] md:h-[200px]"></div>
		<div
			class="mx-auto flex max-w-[1440px] flex-col gap-6 px-4 md:flex-row md:gap-0 md:px-6">
			<h4
				class="font-die-d text-driveway type-display mr-12 flex-2/3 font-medium">
				We’re a Vertically Integrated Company
			</h4>
			<div
				class="md:border-l-driveway type-title font-die-a h-[260px] flex-1/3 font-medium md:border-l-1 md:pl-6 md:font-medium">
				We control our fate by owning every step of the real estate
				development process.
			</div>
		</div>
		<div class="h-[40px]"></div>
	</div>

	<div class="bg-cumulus">
		<div
			class="mx-auto flex max-w-[1440px] flex-col gap-6 px-4 md:flex-row md:gap-0 md:px-6">
			<div
				class="border-t-driveway md:border-l-driveway flex flex-1/3 flex-col gap-6 border-t-1 pt-4 md:mr-6 md:border-t-0 md:border-l-1 md:pt-0 md:pl-6">
				<div class="flex items-center gap-3">
					<div
						class="text-cumulus bg-driveway font-die-a flex min-h-[26px] min-w-[26px] items-center justify-center rounded-full text-[18px] leading-[24px] md:min-h-[28px] md:min-w-[28px] lg:min-h-[28px] lg:min-w-[28px] xl:min-h-[48px] xl:min-w-[48px] xl:text-[24px]">
						1
					</div>
					<div
						class="font-die-d text-driveway type-display font-medium">
						Buy Land
					</div>
				</div>
				<div
					class="bg-driveway/20 aspect-[424/250] h-auto w-full rounded-[2px]">
				</div>
			</div>
			<div
				class="border-t-driveway md:border-l-driveway flex flex-1/3 flex-col gap-6 border-t-1 pt-4 md:mr-6 md:border-t-0 md:border-l-1 md:pt-0 md:pl-6">
				<div class="flex items-center gap-3">
					<div
						class="text-cumulus bg-driveway font-die-a flex min-h-[26px] min-w-[26px] items-center justify-center rounded-full text-[18px] leading-[24px] md:min-h-[28px] md:min-w-[28px] lg:min-h-[28px] lg:min-w-[28px] xl:min-h-[48px] xl:min-w-[48px] xl:text-[24px]">
						2
					</div>
					<div
						class="font-die-d text-driveway type-display font-medium">
						Build Homes
					</div>
				</div>
				<div
					class="bg-driveway/20 aspect-[424/250] h-auto w-full rounded-[2px]">
				</div>
			</div>
			<div
				class="border-t-driveway md:border-l-driveway flex flex-1/3 flex-col gap-6 border-t-1 pt-4 md:border-t-0 md:border-l-1 md:pt-0 md:pl-6">
				<div class="flex items-center gap-3">
					<div
						class="text-cumulus bg-driveway font-die-a flex min-h-[26px] min-w-[26px] items-center justify-center rounded-full text-[18px] leading-[24px] md:min-h-[28px] md:min-w-[28px] lg:min-h-[28px] lg:min-w-[28px] xl:min-h-[48px] xl:min-w-[48px] xl:text-[24px]">
						3
					</div>
					<div
						class="font-die-d text-driveway type-display font-medium">
						Sell Homes
					</div>
				</div>
				<div
					class="bg-driveway/20 aspect-[424/250] h-auto w-full rounded-[2px]">
				</div>
			</div>
		</div>
		<div class="h-[160px] md:h-[200px]"></div>
	</div>

	<div class="bg-cumulus hidden md:block">
		<div class="mx-auto flex max-w-[1440px] px-6">
			<div
				class="bg-driveway/20 mr-6 aspect-[560/515] h-auto w-full flex-2/3 rounded-[2px] md:aspect-[920/720]">
			</div>
			<div
				class="border-l-driveway type-title flex flex-1/3 flex-col border-l-1 pl-6">
				<h4 class="font-die-d text-driveway type-display font-medium">
					End-To-End Tech
				</h4>
				<div class="min-h-[40px] flex-1"></div>
				<Accordion
					items={[
						{
							title: "Building Systems",
							text: "We design and engineer a proprietary, componentized building system, optimized for high-volume manufacturing and adaptable to real-world site conditions."
						},
						{
							title: "Factory",
							text: "We manufacture and assemble every major component in our own factories, using custom machines and tools engineered in-house to automate production and ensure consistent quality."
						},
						{
							title: "Software",
							text: "Our proprietary software orchestrates the entire production stack — tracking materials, analyzing properties, and optimizing tasks in real time across design, manufacturing, and assembly."
						},
						{
							title: "Logistics",
							text: "Each complete building system is designed to fit into a single intermodal container, enabling efficient shipment to any site in the country."
						},z
						{
							title: "Installation",
							text: "Our rowhomes are assembled on-site in days. Simple connections, purpose-built rigs, and repeatable processes make installation safe, fast, and precise."
						}
					]} />
			</div>
		</div>
		<div class="h-[160px] md:h-[200px]"></div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto max-w-[1440px] px-4 md:px-6">
			<div class="border-y-driveway flex items-center border-y-1 py-6">
				<h3
					class="font-die-a text-driveway/60 md:text-driveway type-title font-medium whitespace-nowrap">
					As Featured In
				</h3>
				<div class="min-w-8 flex-1"></div>
				<div
					class="flex min-w-0 flex-col items-end gap-8 md:flex-row md:items-center md:gap-10">
					<img
						src="/images/logo-new-york.svg"
						alt="New York"
						class="max-h-[40px] w-auto shrink translate-y-1" />
					<img
						src="/images/logo-the-atlantic.svg"
						alt="The Atlantic"
						class="max-h-[36px] w-auto shrink -translate-y-1" />
					<img
						src="/images/logo-vox.svg"
						alt="Vox"
						class="max-h-[36px] w-auto shrink -translate-y-1" />
					<img
						src="/images/logo-washington-post.svg"
						alt="The Washington Post"
						class="max-h-[40px] w-auto shrink" />
				</div>
			</div>
			<div class="h-[160px] md:h-[200px]"></div>
		</div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto max-w-[1440px] px-4 md:px-6">
			<h3 class="text-driveway font-die-d type-display font-medium">
				Timeline
			</h3>
		</div>
		<div class="h-4 md:h-6"></div>
		<Timeline
			items={[
				{ year: "2025", text: "Company founded in Austin, Texas." },
				{ year: "2025", text: "Company founded in Austin, Texas." },
				{ year: "2025", text: "Company founded in Austin, Texas." }
			]} />
		<div class="h-[160px] md:h-[200px]"></div>
	</div>

	<div class="bg-cumulus">
		<div
			class="mx-auto flex max-w-[1440px] flex-col px-4 md:flex-row md:px-6">
			<h4
				class="font-die-d text-driveway type-display font-medium md:hidden">
				United We Build
			</h4>
			<div class="h-[24px] md:hidden"></div>
			<div
				class="bg-driveway/20 mr-6 aspect-[560/644] h-auto w-full flex-2/3 rounded-[2px] lg:aspect-[920/800]">
			</div>
			<div
				class="md:border-l-driveway flex flex-1/3 flex-col md:border-l-1 md:pl-6">
				<h4
					class="font-die-d text-driveway type-display hidden font-medium md:block">
					United We Build
				</h4>
				<div class="h-[24px] md:h-[64px]"></div>
				<div class="sticky top-[120px]">
					<div
						class="text-driveway type-title font-die-a font-medium">
						The American Housing Corporation is a growing team of
						engineers in Austin, Texas. We’re looking for hard
						workers to reinvent the most important product in
						America — the family home. If you’re ready to rebuild
						this country using next-generation technology, we’d like
						to meet you.
					</div>
					<div class="h-[64px]"></div>
					<a
						href="/careers"
						class="group font-die-a bg-blue inline-flex cursor-pointer gap-2 self-start rounded-full px-4 py-3 text-[18px] leading-4 text-white">
						<Rollover text="Join Us" />
						<img
							src="./icons/arrow-right-cumulus.svg"
							width="14"
							height="8"
							alt="→" />
					</a>
				</div>
			</div>
		</div>
		<div class="h-[160px] md:h-[200px]"></div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto flex max-w-[1440px] px-4 md:px-6">
			<h5 class="text-red font-die-d type-display font-medium">
				The new home of the American Dream.
			</h5>
		</div>
		<div class="h-6 md:h-[40px]"></div>
	</div>

	<Footer />
</main>

<style>
	@media (width >= 1000px) {
		.shifted-alpha {
			transform: translateY(120px);
			color: var(--color-driveway);
		}

		.shifted-beta {
			transform: translateY(92px);
		}
	}

	@media (width >= 1200px) {
		.shifted-alpha {
			transform: translateY(120px);
			color: var(--color-driveway);
		}

		.shifted-beta {
			transform: translateY(92px);
		}
	}

	@media (width >= 1400px) {
		.shifted-alpha {
			transform: translateY(176px);
			color: var(--color-driveway);
		}

		.shifted-beta {
			transform: translateY(156px);
		}
	}
</style>
