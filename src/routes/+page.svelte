<script lang="ts">
	import { Accordion, Carousel, Logo, Marquee, Timeline } from "$lib";
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
					alt="→" />
			</a>
		</div>
	</div>
</div>

<main>
	<div class="bg-driveway">
		<div class="mx-auto flex h-svh max-w-[1440px] items-end p-4 md:p-6">
			<h1
				class="font-die-d text-cumulus text-[36px] leading-[36px] font-medium md:text-[64px] md:leading-[64px]">
				Saving the<br />
				American Dream
			</h1>
		</div>
	</div>

	<div class="bg-cumulus mx-auto max-w-[1440px]">
		<div class="h-[24px]"></div>
		<div class="flex flex-col gap-4 px-4 md:flex-row md:gap-6 md:px-6">
			<h2
				class="font-die-d text-driveway flex-1/2 text-[36px] leading-[36px] font-medium md:text-[64px] md:leading-[64px]">
				Through All-Out<br />
				Housing Production
			</h2>
			<div class="bg-driveway aspect-[684/552] flex-1/2 rounded-[2px]">
			</div>
		</div>
	</div>

	<div class="bg-cumulus mx-auto max-w-[1440px]">
		<div class="px-4 md:px-6">
			<div class="h-6 md:h-[200px]"></div>
			<div class="flex flex-col gap-4 md:flex-row md:gap-6">
				<div
					class="md:flex-1/3 md:border-l-1 md:border-l-driveway md:pl-6">
					<div
						class="text-driveway font-die-a text-[18px] leading-[21px] font-medium md:text-[24px] md:leading-[24px]">
						We’re building an abundance of beautiful starter homes
						across the United States, in cities where families love
						to live.
					</div>
					<div class="h-[48px] md:h-[64px]"></div>
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
					<div class="md:h-[64px]"></div>
				</div>
				<div class="flex-2/3"></div>
			</div>
			<div class="h-[160px] md:h-[200px]"></div>
		</div>
	</div>
	<div class="bg-cumulus">
		<div class="mx-auto max-w-[1440px] px-4 md:px-6">
			<h3
				class="font-die-a text-driveway text-[18px] leading-[18px] font-medium md:text-[24px] md:leading-[24px]">
				Design
			</h3>
		</div>
		<div class="h-4 md:h-[40px]"></div>
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
		<div class="h-[160px] md:h-[200px]"></div>
		<div
			class="mx-auto flex max-w-[1440px] flex-col gap-6 px-4 md:flex-row md:gap-0 md:px-6">
			<h4
				class="font-die-d text-driveway mr-12 flex-2/3 text-[36px] leading-[36px] font-medium md:text-[64px] md:leading-[64px]">
				We’re a Vertically Integrated Company
			</h4>
			<div
				class="h-[260px] flex-1/3 text-[18px] leading-[21px] font-medium md:border-l-1 md:border-l-driveway md:pl-6 md:text-[24px] md:leading-[24px] md:font-normal">
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
				class="flex flex-1/3 flex-col gap-6 border-t-1 border-t-driveway pt-4 md:mr-6 md:border-t-0 md:border-l-1 md:border-l-driveway md:pt-0 md:pl-6">
				<div class="flex items-center gap-3">
					<div
						class="text-cumulus bg-driveway font-die-a flex min-h-[26px] min-w-[26px] items-center justify-center rounded-full text-[18px] leading-[18px] md:min-h-[48px] md:min-w-[48px] md:text-[24px] md:leading-[24px]">
						1
					</div>
					<div
						class="font-die-d text-driveway text-[36px] leading-[36px] font-medium md:text-[64px] md:leading-[64px]">
						Buy Land
					</div>
				</div>
				<div
					class="bg-driveway aspect-[424/250] h-auto w-full rounded-[2px]">
				</div>
			</div>
			<div
				class="flex flex-1/3 flex-col gap-6 border-t-1 border-t-driveway pt-4 md:mr-6 md:border-t-0 md:border-l-1 md:border-l-driveway md:pt-0 md:pl-6">
				<div class="flex items-center gap-3">
					<div
						class="text-cumulus bg-driveway font-die-a flex min-h-[26px] min-w-[26px] items-center justify-center rounded-full text-[18px] leading-[18px] md:min-h-[48px] md:min-w-[48px] md:text-[24px] md:leading-[24px]">
						2
					</div>
					<div
						class="font-die-d text-driveway text-[36px] leading-[36px] font-medium md:text-[64px] md:leading-[64px]">
						Build Homes
					</div>
				</div>
				<div
					class="bg-driveway aspect-[424/250] h-auto w-full rounded-[2px]">
				</div>
			</div>
			<div
				class="flex flex-1/3 flex-col gap-6 border-t-1 border-t-driveway pt-4 md:border-t-0 md:border-l-1 md:border-l-driveway md:pt-0 md:pl-6">
				<div class="flex items-center gap-3">
					<div
						class="text-cumulus bg-driveway font-die-a flex min-h-[26px] min-w-[26px] items-center justify-center rounded-full text-[18px] leading-[18px] md:min-h-[48px] md:min-w-[48px] md:text-[24px] md:leading-[24px]">
						3
					</div>
					<div
						class="font-die-d text-driveway text-[36px] leading-[36px] font-medium md:text-[64px] md:leading-[64px]">
						Sell Homes
					</div>
				</div>
				<div
					class="bg-driveway aspect-[424/250] h-auto w-full rounded-[2px]">
				</div>
			</div>
		</div>
		<div class="h-[160px] md:h-[200px]"></div>
	</div>

	<div class="bg-cumulus hidden md:block">
		<div class="mx-auto flex max-w-[1440px] px-6">
			<div
				class="bg-driveway mr-6 aspect-[920/644] h-auto w-full flex-2/3 rounded-[2px]">
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
		<div class="h-[160px] md:h-[200px]"></div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto max-w-[1440px] px-4 md:px-6">
			<div class="border-y-driveway flex border-y-1 py-6">
				<h3
					class="font-die-a text-driveway/60 md:text-driveway text-[18px] leading-[18px] font-medium md:text-[24px] md:leading-[24px]">
					As Featured In
				</h3>
				<div class="flex-1"></div>
				<div
					class="flex flex-col gap-6 md:flex-auto md:flex-row md:gap-12">
					<div class="bg-driveway h-[24px] w-32"></div>
					<div class="bg-driveway h-[24px] w-32"></div>
					<div class="bg-driveway h-[24px] w-32"></div>
					<div class="bg-driveway h-[24px] w-32"></div>
					<div class="bg-driveway h-[24px] w-32"></div>
				</div>
			</div>
			<div class="h-[160px] md:h-[200px]"></div>
		</div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto max-w-[1440px] px-4 md:px-6">
			<h3
				class="font-die-a text-driveway text-[18px] leading-[18px] font-medium md:text-[24px] md:leading-[24px]">
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
				class="font-die-d text-driveway text-[36px] leading-[36px] font-medium md:hidden">
				United We Build
			</h4>
			<div class="h-[24px] md:hidden"></div>
			<div
				class="bg-driveway mr-6 aspect-[920/644] h-auto w-full flex-2/3 rounded-[2px]">
			</div>
			<div
				class="flex flex-1/3 flex-col md:border-l-1 md:border-l-driveway md:pl-6">
				<h4
					class="font-die-d text-driveway hidden text-[64px] leading-[64px] font-medium md:block">
					United We Build
				</h4>
				<div class="h-[24px] md:h-[64px]"></div>
				<div
					class="text-driveway text-[18px] leading-[21px] font-medium md:text-[24px] md:leading-[24px] md:font-normal">
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
						alt="→" />
				</a>
			</div>
		</div>
		<div class="h-[160px] md:h-[200px]"></div>
	</div>

	<div class="bg-cumulus">
		<div class="mx-auto flex max-w-[1440px] px-4 md:px-6">
			<h5
				class="text-red font-die-d text-[36px] leading-[36px] font-medium md:text-[64px] md:leading-[64px]">
				Move in. Make babies. Save America.
			</h5>
		</div>
		<div class="h-6 md:h-[40px]"></div>
	</div>

	<div class="bg-blue">
		<div
			class="text-cumulus font-die-a mx-auto flex h-[800px] max-w-[1440px] flex-col p-4 text-[14px] leading-[20px] md:p-6">
			<img
				class="w-full"
				src="/images/american-housing.svg"
				width="1385"
				height="180"
				alt="American Housing" />
			<div class="flex-1"></div>
			<div
				class="flex flex-row-reverse items-start gap-0 md:flex-row md:gap-12">
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
					class="text-cumulus font-die-a flex flex-col gap-6 text-[14px] leading-[20px] md:flex-row md:gap-12">
					<a href="/contact">Contact</a>
					<a href="/mission">Mission</a>
					<a href="/faq">FAQs</a>
					<a href="/research">Research</a>
				</div>
				<div
					class="border-b-cumulus hidden w-[250px] border-b-1 pb-0.5 md:flex">
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
			<div class="h-[64px] md:hidden"></div>
			<div
				class="border-b-cumulus flex border-b-1 pb-0.5 md:hidden md:w-[250px]">
				<input
					class="relative -top-[1.5px] flex-1 appearance-none text-inherit outline-none"
					placeholder="Enter Email"
					type="text" />
				<input
					class="relative -top-[1px] appearance-none"
					type="submit"
					value="Sign up" />
			</div>
			<div class="h-[64px]"></div>
			<div
				class="flex flex-col-reverse font-medium md:flex-row md:font-normal">
				<div>
					© The American Housing Corporation, 2025<br />
					4422 Supply Ct Road, Austin, TX 78744 USA
				</div>
				<div class="min-h-[48px] flex-1 md:h-0"></div>
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
