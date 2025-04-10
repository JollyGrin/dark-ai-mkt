<script lang="ts">
	import { base } from '$app/paths';
	import { page } from '$app/state';
	import ShineBorder from '$lib/components/ShineBorder.svelte';

	const isMarketplace = page.url.pathname === '/';
	const isShop = page.url.pathname === '/shop';
</script>

<div class="bg-brand-fore/0 px-2 py-4">
	<div class="text-brand-highlight container mx-auto flex items-center justify-between font-bold">
		<p>$DARK</p>
		<p>{page.url.pathname}</p>
		<div class="flex items-center gap-4">
			<a href="{base}/">MarketPlace</a>
			<a href="{base}/shop">Shop</a>
			<div class="bg-brand-highlight h-6 w-6 rounded-full"></div>
		</div>
	</div>
</div>
<div class="relative h-0 w-full">
	<ShineBorder />
</div>
