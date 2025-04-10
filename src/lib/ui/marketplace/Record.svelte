<script lang="ts">
	import { MoveDownRight, MoveUpRight } from 'lucide-svelte';

	let {
		isEven = true,
		agent,
		isFirst = false
	}: { isEven: boolean; agent: any; isFirst: boolean } = $props();
</script>

<div
	class="my-1 grid grid-cols-1 items-center gap-1 py-2 md:grid-cols-[3fr_1fr_1fr_1fr]"
	class:mt-0={isFirst}
	class:bg-gradient-to-l={isEven}
	class:to-brand-back={isEven}
	class:from-slate-800={isEven}
>
	<!-- AGENT -->
	<div
		class="border-r-brand-fore/10 flex items-center justify-center gap-4 border-r-1 md:justify-start"
	>
		<div class="relative">
			<img
				alt="ai agent"
				src="https://picsum.photos/seed/{agent.name}/200/250"
				class="aspect-[1] w-[50px] rounded-lg object-cover"
			/>
			<div
				class="bg-brand-back border-brand-fore/10 absolute right-[-5px] bottom-[-5px] grid aspect-[1] w-4 place-items-center rounded border-1 text-xs"
			>
				{#if Math.random() > 0.5}
					<MoveUpRight class="absolute w-3 text-emerald-400" />
				{:else}
					<MoveDownRight class="absolute w-3 text-red-400" />
				{/if}
			</div>
		</div>
		<div class="flex flex-col">
			<p>{agent.name}</p>
			<p class="text-brand-highlight/60 text-xs">Lorem upsum dolorem suhi</p>
		</div>
	</div>

	<!-- PERFORMANCE -->
	<span> tags </span>
	<!-- SHARES -->
	<span> shares </span>
	<!-- PRICE -->
	<span> price </span>
</div>
