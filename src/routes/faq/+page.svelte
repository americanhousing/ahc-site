<script>
	import { Accordion, Footer, Header } from "$lib";
</script>

<Header />

<main>
	<div class="bg-cumulus">
		<div class="h-[110px] md:h-[120px]"></div>
		<div
			class="mx-auto flex min-h-[40vh] max-w-[1440px] flex-col px-4 md:flex-row md:px-6">
			<h1
				class="font-die-d text-driveway type-display font-medium md:hidden">
				Frequently Asked Questions
			</h1>
			<div class="h-[24px] md:hidden"></div>
			<div
				class="bg-driveway/20 mr-6 aspect-[560/800] h-auto w-full flex-5/12 rounded-[2px] lg:aspect-[560/800]">
			</div>
			<div
				class="md:border-l-driveway flex flex-7/12 flex-col md:border-l-1 md:pl-6">
				<h1
					class="font-die-d text-driveway type-display hidden font-medium md:block">
					Frequently Asked Questions
				</h1>
				<div class="min-h-[160px] flex-1 md:min-h-[200px]"></div>
				<Accordion
					color="driveway"
					items={[
						{
							title: "Question?",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						},
						{
							title: "Question?",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						},
						{
							title: "Question?",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						},
						{
							title: "Question?",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						},
						{
							title: "Question?",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						},
						{
							title: "Question?",
							text: "Supporting text goes here in this space like this. Supporting text goes here in this space like this."
						}
					]} />
			</div>
		</div>
		<div class="h-[160px] md:h-[200px]"></div>
	</div>
	<Footer />
</main>
