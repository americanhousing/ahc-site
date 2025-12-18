<script lang="ts">
	import { Footer, Header } from "$lib";

	let visibleElements = $state<Set<string>>(new Set());
	let fadeTargets = $state<Map<string, HTMLElement>>(new Map());

	function didChangeVisibility(entries: IntersectionObserverEntry[]) {
		for (const entry of entries) {
			const id = entry.target.getAttribute("data-fade");

			if (id === null) {
				continue;
			}

			if (entry.isIntersecting === true) {
				visibleElements = new Set([...visibleElements, id]);
			}
		}
	}

	$effect(() => {
		const observer = new IntersectionObserver(didChangeVisibility, {
			threshold: 0.3,
			rootMargin: "0px 0px -100px 0px"
		});

		for (const [, element] of fadeTargets) {
			observer.observe(element);
		}

		return () => {
			observer.disconnect();
		};
	});

	function bindFadeTarget(node: HTMLElement, id: string) {
		fadeTargets.set(id, node);
		fadeTargets = new Map(fadeTargets);

		return {
			destroy() {
				fadeTargets.delete(id);
				fadeTargets = new Map(fadeTargets);
			}
		};
	}
</script>

<Header />

<main>
	<div class="bg-blue min-h-[50vh]">
		<div class="h-[110px] md:h-[120px]"></div>
		<div
			class="mx-auto min-h-[40vh] max-w-[1440px] flex-col px-4 md:flex-row md:px-6">
			<div
				class="bg-driveway/20 aspect-[360/390] h-auto w-full rounded-[2px] md:aspect-[1392/690]">
			</div>
			<div class="h-[24px] md:h-[84px]"></div>
			<img
				class="w-full"
				src="/images/united-we-build.svg"
				width="1328"
				height="160"
				alt="United We Build" />
			<div class="h-[24px] md:h-[84px]"></div>
			<p
				class="type-body md:type-display text-cumulus font-gt-super-book md:text-balance">
				We won independence, expanded freedom, beat a depression at home
				and spread democracy abroad. We united the continent with
				highways, raised skyscrapers, put men on the moon.
			</p>
			<div class="h-[48px] md:h-[84px]"></div>
			<div
				use:bindFadeTarget={"section-1"}
				data-fade="section-1"
				class="flex flex-col opacity-0 transition-all delay-150 duration-1000 ease-out md:flex-row"
				class:opacity-100={visibleElements.has("section-1")}>
				<div class="flex-1/2 md:mr-6">
					<div
						class="bg-driveway/20 mb-3 aspect-[560/644] h-auto w-full rounded-[2px] lg:aspect-[684/855]">
					</div>
				</div>
				<div class="h-[24px] md:hidden"></div>
				<div
					class="bg-cumulus mb-3 hidden min-h-full min-w-[1px] md:block">
				</div>
				<div class="flex-1/2 self-stretch">
					<div class="md:sticky md:top-[120px]">
						<div class="md:pl-6">
							<div
								class="font-die-d text-cumulus type-body md:type-display -translate-y-2 font-medium">
								Over 250 years, a simple truth took form: the
								American Dream is built, not inherited.
							</div>
						</div>
					</div>
				</div>
			</div>
			<div class="h-[48px] md:h-[84px]"></div>
			<p
				use:bindFadeTarget={"body-1"}
				data-fade="body-1"
				class="type-body md:type-display text-cumulus font-gt-super-book opacity-0 transition-all delay-150 duration-1000 ease-out"
				class:opacity-100={visibleElements.has("body-1")}
				class:translate-y-0={visibleElements.has("body-1")}>
				Now it’s our turn to build something worthy of the name
				“American.”
			</p>
			<p
				class="type-body md:type-display text-cumulus font-gt-super-book">
				<br />
			</p>
			<p
				use:bindFadeTarget={"body-2"}
				data-fade="body-2"
				class="type-body md:type-display text-cumulus font-gt-super-book opacity-0 transition-all delay-150 duration-1000 ease-out"
				class:opacity-100={visibleElements.has("body-2")}
				class:translate-y-0={visibleElements.has("body-2")}>
				Today, many who say the American Dream is dead are really
				talking about housing. Too many families can’t afford a starter
				home in the cities they love. From the moment they plan for a
				child until their oldest enters school, they want to stay where
				opportunity and community thrive. But a shortage of homes makes
				that impossible, forcing people to choose between putting down
				roots or starting a family elsewhere.
			</p>
			<div class="h-[48px] md:h-[84px]"></div>
			<div
				use:bindFadeTarget={"section-2"}
				data-fade="section-2"
				class="flex flex-col opacity-0 transition-all delay-150 duration-1000 ease-out md:flex-row"
				class:opacity-100={visibleElements.has("section-2")}>
				<div class="flex-1/2 md:mr-6">
					<div
						class="bg-driveway/20 mb-3 aspect-[560/644] h-auto w-full rounded-[2px] lg:aspect-[684/855]">
					</div>
				</div>
				<div class="h-[24px] md:hidden"></div>
				<div
					class="bg-cumulus mb-3 hidden min-h-full min-w-[1px] md:block">
				</div>
				<div class="flex-1/2 self-stretch">
					<div class="md:sticky md:top-[120px]">
						<div class="md:pl-6">
							<div
								class="font-die-d text-cumulus type-body md:type-display -translate-y-2 font-medium">
								<p>
									When families are priced out, cities hollow
									out. And as cities go, so goes America.
								</p>
								<p><br /></p>
								<p>That’s why we build.</p>
							</div>
						</div>
					</div>
				</div>
			</div>
			<div class="h-[48px] md:h-[84px]"></div>
			<p
				use:bindFadeTarget={"body-3"}
				data-fade="body-3"
				class="type-body md:type-display text-cumulus font-gt-super-book opacity-0 transition-all delay-150 duration-1000 ease-out"
				class:opacity-100={visibleElements.has("body-3")}
				class:translate-y-0={visibleElements.has("body-3")}>
				We’re an organization of engineers, designers, architects, and
				operators who believe housing is the cornerstone of the American
				Dream. Some of us come from construction sites, some from rocket
				factories, some from software labs. But we’re united by a shared
				instinct: make it real.
			</p>
			<p
				class="type-body md:type-display text-cumulus font-gt-super-book">
				<br />
			</p>
			<p
				use:bindFadeTarget={"body-4"}
				data-fade="body-4"
				class="type-body md:type-display text-cumulus font-gt-super-book opacity-0 transition-all delay-150 duration-1000 ease-out"
				class:opacity-100={visibleElements.has("body-4")}
				class:translate-y-0={visibleElements.has("body-4")}>
				Together, we’re applying advanced engineering to increase
				quality and lower cost for the most important product on earth.
				We’re not the first to make this promise — but we’re the first
				to unite technology, manufacturing, and real estate under one
				roof, fully integrated from end to end.
			</p>
			<p
				class="type-body md:type-display text-cumulus font-gt-super-book">
				<br />
			</p>
			<p
				use:bindFadeTarget={"body-5"}
				data-fade="body-5"
				class="type-body md:type-display text-cumulus font-gt-super-book opacity-0 transition-all delay-150 duration-1000 ease-out"
				class:opacity-100={visibleElements.has("body-5")}
				class:translate-y-0={visibleElements.has("body-5")}>
				Total integration gives us total control over what we build, how
				we build, and where we build it. In doing so, we’re not just
				building homes — we’re building a new housing industry: precise,
				scalable, automated, and powered by American ingenuity.
			</p>
			<div class="h-[48px] md:h-[120px]"></div>
			<section
				class="font-die-a"
				use:bindFadeTarget={"how-we-work"}
				data-fade="how-we-work">
				<div
					class=" type-label md:type-subhead border-b-cumulus text-cumulus border-b-1 pb-[16px] opacity-0 transition-all delay-150 duration-1000 ease-out md:pb-[48px]"
					class:opacity-100={visibleElements.has("how-we-work")}>
					Here’s how we work
				</div>
				<div
					class="type-body md:type-headline border-b-cumulus text-cumulus border-b-1 pt-[16px] pb-[16px] font-medium opacity-0 transition-all delay-[250ms] duration-1000 ease-out md:pb-[48px]"
					class:opacity-100={visibleElements.has("how-we-work")}>
					We buy land in great neighborhoods near centers of
					prosperity.
				</div>
				<div
					class="type-body md:type-headline border-b-cumulus text-cumulus border-b-1 pt-[16px] pb-[16px] font-medium opacity-0 transition-all delay-[350ms] duration-1000 ease-out md:pb-[48px]"
					class:opacity-100={visibleElements.has("how-we-work")}>
					We manufacture every component in automated U.S. factories.
				</div>
				<div
					class="type-body md:type-headline border-b-cumulus text-cumulus border-b-1 pt-[16px] pb-[16px] font-medium opacity-0 transition-all delay-[450ms] duration-1000 ease-out md:pb-[48px]"
					class:opacity-100={visibleElements.has("how-we-work")}>
					We design and engineer attractive, modular homes optimized
					for families.
				</div>
				<div
					class="type-body md:type-headline border-b-cumulus text-cumulus border-b-1 pt-[16px] pb-[16px] font-medium opacity-0 transition-all delay-[550ms] duration-1000 ease-out md:pb-[48px]"
					class:opacity-100={visibleElements.has("how-we-work")}>
					We deliver the building parts across the nation and assemble
					on-site.
				</div>
				<div
					class="type-body md:type-headline border-b-cumulus text-cumulus border-b-1 pt-[16px] pb-[16px] font-medium opacity-0 transition-all delay-[650ms] duration-1000 ease-out md:pb-[48px]"
					class:opacity-100={visibleElements.has("how-we-work")}>
					We sell and rent these homes directly to people.
				</div>
			</section>
			<div class="h-[48px] md:h-[120px]"></div>

			<p
				use:bindFadeTarget={"body-6"}
				data-fade="body-6"
				class="type-body md:type-display text-cumulus font-gt-super-book opacity-0 transition-all delay-150 duration-1000 ease-out"
				class:opacity-100={visibleElements.has("body-6")}
				class:translate-y-0={visibleElements.has("body-6")}>
				We’re starting by perfecting the rowhouse, the original American
				urban home. Compact, walkable, and rooted in place, rowhouses
				make ideal starter homes for families who want city life without
				sacrificing space, privacy, or quality.
			</p>
			<p
				class="type-body md:type-display text-cumulus font-gt-super-book">
				<br />
			</p>
			<p
				use:bindFadeTarget={"body-7"}
				data-fade="body-7"
				class="type-body md:type-display text-cumulus font-gt-super-book opacity-0 transition-all delay-150 duration-1000 ease-out"
				class:opacity-100={visibleElements.has("body-7")}
				class:translate-y-0={visibleElements.has("body-7")}>
				This is just the beginning of a larger vision. We imagine
				thriving neighborhoods and entire cities where families can stay
				and grow. Where parents find opportunity and children find
				friends. Where architecture is beautiful and neighbors look out
				for each other.
			</p>
			<p
				class="type-body md:type-display text-cumulus font-gt-super-book">
				<br />
			</p>
			<p
				use:bindFadeTarget={"body-8"}
				data-fade="body-8"
				class="type-body md:type-display text-cumulus font-gt-super-book opacity-0 transition-all delay-150 duration-1000 ease-out"
				class:opacity-100={visibleElements.has("body-8")}
				class:translate-y-0={visibleElements.has("body-8")}>
				Because this is more than housing. It’s a new national project
				to secure our future.
			</p>
			<div class="h-[48px] md:h-[84px]"></div>
			<div
				use:bindFadeTarget={"section-3"}
				data-fade="section-3"
				class="flex flex-col opacity-0 transition-all delay-150 duration-1000 ease-out md:flex-row"
				class:opacity-100={visibleElements.has("section-3")}>
				<div class="flex-1/2 md:mr-6">
					<div
						class="bg-driveway/20 mb-3 aspect-[560/644] h-auto w-full rounded-[2px] lg:aspect-[684/855]">
					</div>
				</div>
				<div class="h-[24px] md:hidden"></div>
				<div
					class="bg-cumulus mb-3 hidden min-h-full min-w-[1px] md:block">
				</div>
				<div class="flex-1/2 self-stretch">
					<div class="md:sticky md:top-[120px]">
						<div class="md:pl-6">
							<div
								class="text-cumulus type-body md:type-display -translate-y-2 font-medium">
								<p>
									Block by block, city by city, let’s build a
									new home for the American Dream.
								</p>
							</div>
						</div>
					</div>
				</div>
			</div>
			<div class="h-[110px] md:h-[240px]"></div>
		</div>
	</div>
	<Footer bg="cumulus" fg="red" />
</main>

<style>
	:global(.type-display),
	:global(.type-headline) {
		line-height: 1.1;
	}
</style>
