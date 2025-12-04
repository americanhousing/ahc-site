<svelte:head>
	<script
		id="luma-checkout"
		src="https://embed.lu.ma/checkout-button.js"></script>
</svelte:head>

<div
	class="mx-auto box-border flex min-h-screen max-w-[1440px] gap-6 px-4 md:px-6">
	<div class="flex min-w-96 flex-1/3 flex-col pt-6">
		<img
			src="/images/logo-color.svg"
			width="101"
			height="51"
			alt="The American Housing Corporation" />
		<div class="h-6 md:h-8"></div>

		<h1 class="font-die-d text-[48px] font-medium md:text-[64px]">
			Open House
		</h1>

		<div class="hidden min-h-2 flex-1 md:block"></div>
		<div
			class="bg-driveway/30 mb-4 aspect-[360/285] h-auto w-full rounded-[2px] md:hidden">
		</div>

		<div
			class="flex flex-col gap-2 text-[18px] leading-[24px] md:gap-4 md:text-[24px]">
			<div class="text-driveway/60 font-medium">
				American Housing Launch Event
			</div>
			<div class="text-driveway font-medium">
				The American Housing Corporation is excited to invite you to an
				exclusive preview of our first house prototype and the upcoming
				product lineup in our Austin, TX factory.
			</div>
		</div>

		<div class="bg-driveway my-2 min-h-[0.5px] md:my-4"></div>
		<div
			class="flex flex-col gap-2 text-[18px] leading-[24px] md:gap-4 md:text-[24px]">
			<div class="text-driveway/60 font-medium">Date & Time</div>
			<div class="text-driveway font-medium">
				Wednesday, January 21, 2026<br />
				4-7pm
			</div>
		</div>

		<div class="bg-driveway my-2 min-h-[0.5px] md:my-4"></div>
		<div
			class="flex flex-col gap-2 text-[18px] leading-[24px] md:gap-4 md:text-[24px]">
			<div class="text-driveway/60 font-medium">Location</div>
			<div class="text-driveway font-medium">Register to see address</div>
		</div>

		<div class="bg-driveway my-2 min-h-[0.5px] md:my-4"></div>
		<div class="min-h-18 md:min-h-16"></div>
		<div class="sticky bottom-6 h-0">
			<a
				class="font-die-a bg-blue hover:bg-blue-dark absolute bottom-full flex cursor-pointer justify-center gap-2 rounded-full px-4 py-3 text-[18px] leading-4 text-white md:self-start"
				href="https://luma.com/event/evt-Kqb67T3Xqzx4OIh"
				data-luma-action="checkout"
				data-luma-event-id="evt-Kqb67T3Xqzx4OIh">
				RSVP
				<img
					src="/icons/arrow-right.svg"
					width="14"
					height="8"
					alt="RSVP" />
			</a>
		</div>
	</div>
	<div class="hidden flex-2/3 md:block">
		<div class="sticky top-0 box-border h-screen py-6">
			<div class="bg-driveway/30 h-full rounded-[2px]"></div>
		</div>
	</div>
</div>
