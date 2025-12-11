<script lang="ts">
	type Props = {
		text: string;
	};

	let { text }: Props = $props();
</script>

<span class="relative overflow-hidden">
	<span
		class="inline-block transition-all duration-150 group-hover:translate-y-[-1em] group-hover:opacity-0">
		{text}
	</span>
	<span
		class="pointer-events-none absolute top-0 left-0 inline-block translate-y-[1em] opacity-0 transition-all duration-150 group-hover:translate-none group-hover:opacity-100">
		{text}
	</span>
</span>
