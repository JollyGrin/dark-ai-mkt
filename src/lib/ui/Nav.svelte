<script lang="ts">
	import { base } from '$app/paths';
	import { page } from '$app/state';
	import ShineBorder from '$lib/components/ShineBorder.svelte';
	import { FileQuestion, ShieldQuestion } from 'lucide-svelte';

	const isMarketplace = $derived(page.url.pathname === base + '/');
	const isShop = $derived(page.url.pathname === base + '/shop');
</script>

<div class="bg-brand-fore/0 px-2 py-4">
	<div
		class="text-brand-highlight container mx-auto flex items-center justify-center font-bold sm:justify-between"
	>
		<a href="https://www.darkresearch.ai" class="hidden sm:inline"
			>$DARK <span class="text-xs font-thin">plays <i>Dark Forest</i></span></a
		>
		<div class="flex items-center gap-4">
			<a
				href="{base}/"
				class:text-brand-fore={isMarketplace}
				class:hover:opacity-70={!isMarketplace}
			>
				MarketPlace
			</a>
			<a href="{base}/shop" class:text-brand-fore={isShop} class:hover:opacity-70={!isShop}>Shop</a>
			<a
				href="https://x.com/edgarpavlovsky/status/1909400326828179674?s=46"
				target="_blank"
				class="text-xs font-thin hover:opacity-70"><ShieldQuestion /></a
			>
			<button
				class="border-brand-highlight/50 text-brand-fore hover:border-brand-fore rounded border-1 px-2 py-1 font-normal transition-all"
			>
				Connect
			</button>
		</div>
	</div>
</div>
<div class="relative z-20 mb-[2px] h-0 w-full">
	<ShineBorder />
</div>
