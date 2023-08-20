<script lang="ts">
	import Carousel from '$lib/components/Carousel.svelte';
	import ProductCard from '$lib/components/ProductCard.svelte';
	import FeMouse from '~icons/fe/mouse';
	const products = [
		{
			img: '/images/products/0.webp',
			alt: '',
			title: 'High Quality Beef',
			subtitle: 'Raised to Order',
			icon: 'beef',
			description:
				"We'll raise your beef the right way with options on genetics and finishing. Call today for availability and to get on the waiting list.",
			longDescription:
				"We have several herds in the Lewis County area with different genetics and types of pasture. To maintain the highest quality we don't overpopulate our fields, so we limit our capacity. For this reason we keep a waiting list. Our customers know that the best is worth waiting for, and our quality doesn't disappoint. Occasionally an animal doesn't produce to our standards so we keep a small herd reserved to fill orders in these cases. We take our time raising, finishing, and aging our product to maintain a strict and refined process. We work on the timeline of the animal, not the customer. Trust us, the difference is clear in the results."
		},
		{
			img: '/images/products/1.webp',
			alt: '',
			title: 'Pasture Leasing',
			subtitle: undefined,
			icon: 'location',
			description:
				'Lease your land to trustworthy and humane ranchers and oversee your animals throughout their life',
			longDescription:
				"We don't like to reveal our exact process but we are transparent about what makes the quality. If you have good acreage, want to lease it, and want to be part of our network we'll show you how to maximize the potential of your pasture. To maintain our quality we are selective in who we work with and strict in our process, but if you truly care about the life of the animals and maintaining the highest quality of food for your family then give us a call. Whether or not your land qualifies, we'd be happy to talk with you and love to help fellow small farmers."
		}
	];
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
	<!-- Products -->
	<div class="flex flex-col gap-4 px-4 pt-4 text-center md:px-0">
		<h2 class="text-4xl font-semibold">What we do</h2>
		<div class="flex flex-col justify-center gap-9 md:flex-row md:gap-1">
			{#each products as product}
				<ProductCard {...product} />
			{/each}
		</div>
	</div>
