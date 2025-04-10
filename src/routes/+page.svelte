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
	<div class="grid grid-cols-[3fr_1fr_1fr_1fr] gap-1">
		<span class="bg-red-500"> Agent </span>
		<span class="bg-red-500"> Performance </span>
		<span class="bg-red-500"> Available Shares </span>
		<span class="bg-red-500"> Prices </span>
	</div>

	{#each agents as agent}
		<div class="grid grid-cols-[3fr_1fr_1fr_1fr] gap-1">
			<span class=""> {agent.name} </span>
		</div>
	{/each}
</div>
