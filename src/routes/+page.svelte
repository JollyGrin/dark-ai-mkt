<script lang="ts">
	import Marquee from '$lib/components/Marquee.svelte';
	import { SOL_SYMBOL } from '$lib/symbols';
	import Nav from '$lib/ui/Nav.svelte';
	import { MoveDownRight, MoveUpRight } from 'lucide-svelte';

	const agents = Array.from({ length: 20 }).map((_, i) => ({ name: `Agent${i}` }));
</script>

<Nav />

<div class="container mx-auto">
	<div class="py-2">
		{#snippet eachSnippet(item: any)}
			<div
				class="mx-1 flex aspect-[1/1.25] w-[125px] flex-col justify-end gap-2 rounded-lg bg-cover bg-no-repeat p-1 transition-all hover:saturate-150"
				style="background: url('https://picsum.photos/seed/{item.name}/200/250');"
			>
				<p class="font-bold">{item.name}</p>
				<div class="flex gap-1 text-xs">
					<span class="rounded-lg p-1 backdrop-blur-md">76%</span>
					<span class="rounded-lg p-1 backdrop-blur-md">0.3{SOL_SYMBOL}</span>
				</div>
			</div>
		{/snippet}
		<Marquee items={agents.splice(0, 5)} {eachSnippet} />
	</div>
</div>

<div class="container mx-auto">
	<div
		class="border-b-brand-fore/10 text-brand-highlight hidden grid-cols-[3fr_1fr_1fr_1fr] gap-1 border-b-1 pb-1 text-xs font-bold tracking-wide uppercase md:grid"
	>
		<span class="border-r-brand-fore/10 border-r-1"> Agent </span>
		<span> Performance </span>
		<span> Available Shares </span>
		<span> Prices </span>
	</div>

	{#each agents as agent, i (i)}
		{@const isEven = i % 2 == 0}
		<div
			class="my-1 grid grid-cols-1 gap-1 py-2 md:grid-cols-[3fr_1fr_1fr_1fr]"
			class:mt-0={i === 0}
			class:bg-gradient-to-l={isEven}
			class:to-brand-back={isEven}
			class:from-slate-800={isEven}
		>
			<!-- AGENT -->
			<div class="border-r-brand-fore/10 flex items-center gap-4 border-r-1">
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
			<span> performance tags </span>
			<!-- SHARES -->
			<span> shares </span>
			<!-- PRICE -->
			<span> price </span>
		</div>
	{/each}
</div>
