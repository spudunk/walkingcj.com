<script lang="ts">
	import MaterialSymbolsCallOutline from '~icons/material-symbols/call-outline';

	import { scrolled } from '$lib/stores';
	import Logo from './Logo.svelte';

	let scrollVal = false;

	scrolled.subscribe((val) => {
		scrollVal = val;
	});
</script>

<nav
	class={`fixed left-0 top-0 z-10 flex w-full flex-row items-center justify-between gap-2 bg-black px-4 py-2 font-poppins text-white transition-all duration-500 ${
		scrollVal ? 'bg-opacity-90 text-xl sm:text-2xl ' : 'bg-opacity-25 text-2xl sm:text-4xl'
	}`}
>
	<div class="flex flex-row items-center gap-5">
		<Logo class="drop-shadow-2xl transition-colors" />
		<span class="hidden md:block">Walking CJ Ranch</span>
	</div>
	<!-- desktop/tablet -->
	<a
		class="hidden h-full items-center gap-2 rounded-lg bg-red-700 px-2 py-2 text-lg md:flex"
		href="#contact"
	>
		<MaterialSymbolsCallOutline />
		Contact Us
	</a>
	<!-- mobile -->
	<a
		class="flex h-full items-center gap-2 rounded-lg bg-red-700 px-2 py-1 text-lg md:hidden"
		href="tel:3602695572"
	>
		<MaterialSymbolsCallOutline />
		Call Us
	</a>
</nav>
