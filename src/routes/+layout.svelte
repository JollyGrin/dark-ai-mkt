<script lang="ts">
	import Nav from '$lib/ui/Nav.svelte';
	import '../app.css';

	let { children } = $props();
</script>

<Nav />
<div class="h-[calc(100svh-59px)] overflow-y-scroll">
	{@render children()}
</div>
