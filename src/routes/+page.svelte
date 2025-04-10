<script lang="ts">
	import Marquee from '$lib/components/Marquee.svelte';
	import { SOL_SYMBOL } from '$lib/symbols';

	const agents = Array.from({ length: 20 }).map((_, i) => ({ name: `Agent${i}` }));
</script>

<div class="bg-brand-fore/10 border-b-brand-fore/20 border-b-1 px-2 py-4">
	<div class=" container mx-auto flex justify-between">
		<p>DARK</p>
		<div class="flex items-center gap-4">
			<p>Marketplace</p>
			<p>Powerup Shop</p>
			<div class="bg-brand-fore/50 h-6 w-6 rounded-full"></div>
		</div>
	</div>
</div>

<div class="container mx-auto">
	<div class="py-2">
		{#snippet eachSnippet(item: any)}
			<div
				class="mx-1 flex aspect-[1/1.25] w-[125px] flex-col justify-end gap-2 rounded-lg bg-cover bg-no-repeat p-1"
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
