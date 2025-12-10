<script lang="ts">
	import { Accordion, Carousel, Logo, Marquee, Timeline } from "$lib";
</script>

<div class="fixed top-0 z-10 w-screen">
	<div class="bg-cumulus/20 backdrop-blur-lg">
		<Marquee items={["$6b raised in series A"]} />
	</div>
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
			<h3
				class="font-die-a text-driveway text-[24px] leading-[24px] font-medium">
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
				class="font-die-d text-driveway mr-12 flex-2/3 text-[64px] leading-[64px] font-medium">
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
						class="font-die-d text-driveway text-[64px] leading-[64px] font-medium">
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
						class="font-die-d text-driveway text-[64px] leading-[64px] font-medium">
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
						class="font-die-d text-driveway text-[64px] leading-[64px] font-medium">
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
				<h4
					class="font-die-d text-driveway text-[64px] leading-[64px] font-medium">
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
				<h3
					class="font-die-a text-driveway text-[24px] leading-[24px] font-medium">
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

	<div class="bg-cumulus">
		<div class="mx-auto max-w-[1440px] px-6">
			<h3
				class="font-die-a text-driveway text-[24px] leading-[24px] font-medium">
				Timeline
			</h3>
		</div>
		<div class="h-6"></div>
		<Timeline
			items={[
				{ year: "2025", text: "Company founded in Austin, Texas." },
				{ year: "2025", text: "Company founded in Austin, Texas." },
				{ year: "2025", text: "Company founded in Austin, Texas." }
			]} />
		<div class="h-[200px]"></div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto flex max-w-[1440px] px-6">
			<div
				class="bg-driveway mr-6 aspect-[920/644] h-auto w-full flex-2/3">
			</div>
			<div
				class="border-l-driveway flex flex-1/3 flex-col border-l-1 pl-6 text-[24px] leading-[24px]">
				<h4
					class="font-die-d text-driveway text-[64px] leading-[64px] font-medium">
					United We Build
				</h4>
				<div class="h-[64px]"></div>
				<div
					class="text-driveway text-[24px] leading-[24px] font-medium">
					The American Housing Corporation is a growing team of
					engineers in Austin, Texas. We’re looking for hard workers
					to reinvent the most important product in America — the
					family home. If you’re ready to rebuild this country using
					next-generation technology, we’d like to meet you.
				</div>
				<div class="h-[64px]"></div>
				<a
					href="/careers"
					class="font-die-a bg-blue inline-flex cursor-pointer gap-2 self-start rounded-full px-4 py-3 text-[18px] leading-4 text-white">
					Join Us
					<img
						src="./icons/arrow-right-white.svg"
						width="14"
						height="8"
						alt="RSVP" />
				</a>
			</div>
		</div>
		<div class="h-[200px]"></div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto flex max-w-[1440px] px-6">
			<h5 class="text-red text-[64px] leading-[64px] font-medium">
				Move in. Make babies. Save America.
			</h5>
		</div>
		<div class="h-[40px]"></div>
	</div>

	<div class="bg-blue">
		<div
			class="text-cumulus font-die-a mx-auto flex h-[800px] max-w-[1440px] flex-col p-6 text-[14px] leading-[20px]">
			<img
				class="w-full"
				src="/images/american-housing.svg"
				width="1385"
				height="180"
				alt="American Housing" />
			<div class="flex-1"></div>
			<div class="flex gap-12">
				<div class="flex items-center gap-6">
					<img
						src="/icons/social-linkedin.svg"
						width="18"
						height="18"
						alt="Linkedin" />
					<img
						src="/icons/social-x.svg"
						width="20"
						height="18"
						alt="X" />
					<img
						src="/icons/social-instagram.svg"
						width="18"
						height="18"
						alt="Instagram" />
				</div>
				<div class="flex-1"></div>
				<div
					class="text-cumulus font-die-a flex gap-12 text-[14px] leading-[20px]">
					<a href="/contact">Contact</a>
					<a href="/mission">Mission</a>
					<a href="/faq">FAQs</a>
					<a href="/research">Research</a>
				</div>
				<div class="border-b-cumulus flex w-[250px] border-b-1 pb-0.5">
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
			<div class="h-[64px]"></div>
			<div class="flex">
				<div>
					© The American Housing Corporation, 2025<br />
					4422 Supply Ct Road, Austin, TX 78744 USA
				</div>
				<div class="flex-1"></div>
				<div class="flex items-center gap-6">
					<img
						src="/images/flag-cumulus.svg"
						width="52"
						height="30"
						alt="" />
					<span>Always made<br />in the USA</span>
				</div>
			</div>
		</div>
	</div>
</main>
