<script lang="ts">
	import { Accordion, Carousel, Logo } from "$lib";
</script>

<div class="fixed top-0 w-screen">
	<div class="bg-cumulus/20 h-[50px] px-4 backdrop-blur-lg"></div>
	<div class="relative mx-auto w-full max-w-[1440px]">
		<Logo />
		<div class="absolute top-6 right-6 flex h-[50px] items-center">
			<a
				href="/careers"
				class="bg-cumulus text-driveway flex gap-2 rounded-full px-4 py-2 text-[18px] leading-[24px]">
				Careers
				<img
					src="/icons/arrow-right-driveway.svg"
					width="12"
					height="10"
					alt="→" />
			</a>
		</div>
	</div>
</div>

<main>
	<div class="bg-driveway">
		<div class="mx-auto flex h-screen max-w-[1440px] items-end p-6">
			<h1
				class="font-die-d text-cumulus text-[64px] leading-[64px] font-medium">
				Saving the<br />
				American Dream
			</h1>
		</div>
	</div>

	<div class="bg-cumulus mx-auto max-w-[1440px]">
		<div class="h-[24px]"></div>
		<div class="flex gap-6 px-6">
			<h2
				class="font-die-d text-driveway flex-1/2 text-[64px] leading-[64px] font-medium">
				Through All-Out<br />
				Housing Production
			</h2>
			<div class="bg-driveway aspect-[684/552] flex-1/2 rounded-[2px]">
			</div>
		</div>
	</div>

	<div class="bg-cumulus mx-auto max-w-[1440px]">
		<div class="px-6">
			<div class="h-[200px]"></div>
			<div class="flex gap-6">
				<div class="border-l-driveway flex-1/3 border-l-1 pl-6">
					<div
						class="text-driveway font-die-a text-[24px] leading-[24px] font-medium">
						We’re building an abundance of beautiful starter homes
						across the United States, in cities where families love
						to live.
					</div>
					<div class="h-[64px]"></div>
					<a
						class="text-blue font-die-a flex items-center gap-2 text-[18px] leading-[24px] font-normal"
						href="/mission">
						Our Mission
						<img
							src="/icons/arrow-right-blue.svg"
							width="12"
							height="10"
							alt="→" />
					</a>
					<div class="h-[64px]"></div>
				</div>
				<div class="flex-2/3"></div>
			</div>
			<div class="h-[200px]"></div>
		</div>
	</div>
	<div class="bg-cumulus">
		<div class="mx-auto max-w-[1440px] px-6">
			<h3 class="font-die-a text-[24px] leading-[24px] font-medium">
				Design
			</h3>
		</div>
		<div class="h-[40px]"></div>
		<Carousel
			images={[
				"https://picsum.photos/1440/1000",
				"https://picsum.photos/1440/1200",
				"https://picsum.photos/1440/1300"
			]}
			marginSize={0.1}
			gap={24} />
	</div>

	<div class="bg-cumulus">
		<div class="h-[200px]"></div>
		<div class="mx-auto flex max-w-[1440px] px-6">
			<h4
				class="font-die-d mr-12 flex-2/3 text-[64px] leading-[64px] font-medium">
				We’re a Vertically Integrated Company
			</h4>
			<div
				class="border-l-driveway h-[260px] flex-1/3 border-l-1 pl-6 text-[24px] leading-[24px]">
				We control our fate by owning every step of the real estate
				development process.
			</div>
		</div>
		<div class="h-[40px]"></div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto flex max-w-[1440px] px-6">
			<div
				class="border-l-driveway mr-6 flex flex-1/3 flex-col gap-6 border-l-1 pl-6">
				<div class="flex items-center gap-3">
					<div
						class="text-cumulus bg-driveway font-die-a flex min-h-[48px] min-w-[48px] items-center justify-center rounded-full text-[24px] leading-[24px]">
						1
					</div>
					<div
						class="font-die-d text-[64px] leading-[64px] font-medium">
						Buy Land
					</div>
				</div>
				<div class="bg-driveway aspect-[424/250] h-auto w-full"></div>
			</div>
			<div
				class="border-l-driveway mr-6 flex flex-1/3 flex-col gap-6 border-l-1 pl-6">
				<div class="flex items-center gap-3">
					<div
						class="text-cumulus bg-driveway font-die-a flex min-h-[48px] min-w-[48px] items-center justify-center rounded-full text-[24px] leading-[24px]">
						2
					</div>
					<div
						class="font-die-d text-[64px] leading-[64px] font-medium">
						Build Homes
					</div>
				</div>
				<div class="bg-driveway aspect-[424/250] h-auto w-full"></div>
			</div>
			<div
				class="border-l-driveway flex flex-1/3 flex-col gap-6 border-l-1 pl-6">
				<div class="flex items-center gap-3">
					<div
						class="text-cumulus bg-driveway font-die-a flex min-h-[48px] min-w-[48px] items-center justify-center rounded-full text-[24px] leading-[24px]">
						3
					</div>
					<div
						class="font-die-d text-[64px] leading-[64px] font-medium">
						Sell Homes
					</div>
				</div>
				<div class="bg-driveway aspect-[424/250] h-auto w-full"></div>
			</div>
		</div>
		<div class="h-[200px]"></div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto flex max-w-[1440px] px-6">
			<div
				class="bg-driveway mr-6 aspect-[920/644] h-auto w-full flex-2/3">
			</div>
			<div
				class="border-l-driveway flex flex-1/3 flex-col border-l-1 pl-6 text-[24px] leading-[24px]">
				<h4 class="font-die-d text-[64px] leading-[64px] font-medium">
					End-To-End Tech
				</h4>
				<div class="flex-1"></div>
				<Accordion
					items={[
						{
							title: "Building Systems",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						},
						{
							title: "Factory",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						},
						{
							title: "Logistics",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						},
						{
							title: "Installation",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						},
						{
							title: "Software",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						}
					]} />
			</div>
		</div>
		<div class="h-[200px]"></div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto max-w-[1440px] px-6">
			<div class="border-y-driveway flex gap-12 border-y-1 py-6">
				<h3 class="font-die-a text-[24px] leading-[24px] font-medium">
					As Featured In
				</h3>
				<div class="flex-1"></div>
				<div class="bg-driveway h-[24px] w-32"></div>
				<div class="bg-driveway h-[24px] w-32"></div>
				<div class="bg-driveway h-[24px] w-32"></div>
				<div class="bg-driveway h-[24px] w-32"></div>
				<div class="bg-driveway h-[24px] w-32"></div>
			</div>
			<div class="h-[200px]"></div>
		</div>
	</div>
</main>
