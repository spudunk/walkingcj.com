<script lang="ts">
	import MdiPhone from '~icons/mdi/phone';

	import { scrolled } from '$lib/stores';
	import Logo from './Logo.svelte';
	import LogoFacebook from '~icons/logos/facebook';
	import { data } from '$lib';

	let scrollVal = false;

	scrolled.subscribe((val) => {
		scrollVal = val;
	});
</script>

<nav
	class={`fixed left-0 top-0 z-50 flex w-full flex-row items-center justify-between gap-2 bg-black px-4 py-2 font-poppins text-white transition-all duration-500 ${
		scrollVal ? 'bg-opacity-90 text-xl sm:text-2xl ' : 'bg-opacity-25 text-2xl sm:text-4xl'
	}`}
>
	<div class="flex flex-row items-center gap-5">
		<Logo class="drop-shadow-2xl transition-colors" />
		<span class="hidden md:block">Walking CJ Ranch</span>
	</div>

	<div class="flex flex-row items-center gap-5">
		<a href={data.facebook}>
			<LogoFacebook alt="Link to Walking CJ Facebook"/>
		</a>

		<a
			class="hidden h-full items-center gap-2 rounded-lg bg-red-700 px-2 py-2 text-lg transition-colors hover:bg-red-600 md:flex"
			href="#contact"
		>
			<MdiPhone />
			Contact Us
		</a>
		<!-- mobile -->
		<a
			class="flex h-full items-center gap-2 rounded-lg bg-red-700 px-2 py-1 text-lg transition-colors hover:bg-red-600 md:hidden"
			href={data.phoneLink}
		>
			<MdiPhone />
			Call Us
		</a>
		<!-- desktop/tablet -->
	</div>
</nav>
