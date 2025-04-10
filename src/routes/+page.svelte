<script lang="ts">
	import Marquee from '$lib/components/Marquee.svelte';
	import ShineBorder from '$lib/components/ShineBorder.svelte';
	import { SOL_SYMBOL } from '$lib/symbols';

	const agents = Array.from({ length: 20 }).map((_, i) => ({ name: `Agent${i}` }));
</script>

<div class="bg-brand-fore/0 px-2 py-4">
	<div class="container mx-auto flex items-center justify-between">
		<p>$DARK</p>
		<div class="flex items-center gap-4">
			<p>Marketplace</p>
			<p>Powerup Shop</p>
			<div class="bg-brand-fore/50 h-6 w-6 rounded-full"></div>
		</div>
	</div>
</div>
<div class="relative h-0 w-full">
	<ShineBorder />
</div>

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
		class="border-b-brand-fore/10 text-brand-fore/50 grid grid-cols-[3fr_1fr_1fr_1fr] gap-1 border-b-1 pb-1 text-xs font-bold tracking-wide uppercase"
	>
		<span class="border-r-brand-fore/10 border-r-1"> Agent </span>
		<span> Performance </span>
		<span> Available Shares </span>
		<span> Prices </span>
	</div>

	{#each agents as agent, i (i)}
		{@const isEven = i % 2 == 0}
		<div
			class="my-1 grid grid-cols-[3fr_1fr_1fr_1fr] gap-1 py-2"
			class:mt-0={i === 0}
			class:bg-gradient-to-l={isEven}
			class:to-brand-back={isEven}
			class:from-gray-800={isEven}
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
						class="bg-brand-back border-brand-fore/30 absolute right-[-5px] bottom-0 rounded border-1 px-1 text-xs"
					>
						H
					</div>
				</div>
				<div class="flex flex-col">
					<p>{agent.name}</p>
					<p class="text-xs opacity-30">Lorem upsum dolorem suhi</p>
				</div>
			</div>

			<!-- PERFORMANCE -->
			<!-- SHARES -->
			<!-- PRICE -->
		</div>
	{/each}
</div>
