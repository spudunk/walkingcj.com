<script lang="ts">
	import { crossfade } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';
	import { onMount } from 'svelte';

	const images = [
		{ id: 0, imagePath: '/images/carousel/0.webp', alt: '' },
		{ id: 1, imagePath: '/images/carousel/1.webp', alt: '' },
		{ id: 2, imagePath: '/images/carousel/2.webp', alt: '' },
		{ id: 3, imagePath: '/images/carousel/3.webp', alt: '' }
	];

	let carouselIndex = 0;

	onMount(() => {
		setInterval(() => {
			carouselIndex = (carouselIndex + 1) % images.length;
		}, 5000);
	});

	const [send, recieve] = crossfade({
		duration: 2000,
		easing: quintOut
	});
</script>

<svelte:head>
	{#each images as image}
		<link rel="preload" href={image.imagePath} as="image" />
	{/each}
</svelte:head>

{#each images as image, i}
	{#if i === carouselIndex}
		<img
			class="absolute left-0 top-0 -z-10 h-[95vh] w-screen object-cover"
			src={image.imagePath}
			in:send={{ key: 'carousel' }}
			out:recieve={{ key: 'carousel' }}
			alt={image.alt}
			aria-hidden="true"
		/>
	{/if}
{/each}
