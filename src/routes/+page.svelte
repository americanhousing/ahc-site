<script lang="ts">
	import { Carousel } from "$lib";
</script>

<div class="bg-driveway">
	<div class="mx-auto flex max-w-[1440px] items-end p-6">
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
		<div class="bg-driveway aspect-[684/552] flex-1/2 rounded-[2px]"></div>
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
					across the United States, in cities where families love to
					live.
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
	<div class="mx-auto flex max-w-[1440px] gap-6 px-6">
		<h4 class="font-die-d flex-2/3 text-[64px] leading-[64px] font-medium">
			We’re a Vertically Integrated Company
		</h4>
		<div
			class="border-l-driveway h-[260px] flex-1/3 border-l-1 pl-6 text-[24px] leading-[24px]">
			We control our fate by owning every step of the real estate
			development process.
		</div>
	</div>
</div>
