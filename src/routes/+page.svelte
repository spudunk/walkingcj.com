<script lang="ts">
	import Carousel from '$lib/components/Carousel.svelte';
	import FeMouse from '~icons/fe/mouse';
</script>

<!-- HERO -->
<div class="relative">
	<Carousel />
	<div class="flex h-[95vh] w-screen items-center justify-center gap-2 bg-black bg-opacity-50">
		<h1 class="stroke text-shadow-2xl rounded-lg px-4 py-2 text-center text-3xl text-white">
			<span class="text-5xl font-semibold text-red-700">HIGH QUALITY BEEF</span>
			<br />raised with a <span class="font-semibold text-red-700">high quality</span> life
		</h1>

		<!-- <FeMouse class="absolute bottom-16 mx-auto animate-bounce text-5xl text-white" /> -->
	</div>
</div>
