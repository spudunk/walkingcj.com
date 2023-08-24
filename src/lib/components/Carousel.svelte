<script lang="ts">
	import { crossfade } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';
	import { onMount } from 'svelte';
	// import { Image } from '@unpic/svelte';
	import { transformUrl } from 'unpic';

	let images = [
		{
			id: 0,
			imagePath:
				'https://res.cloudinary.com/dt9pi5obp/image/upload/v1692807832/walkingcj/IMG_9453_rvdvim.heic',
			alt: ''
		},
		{
			id: 1,
			imagePath:
				'https://res.cloudinary.com/dt9pi5obp/image/upload/v1692807808/walkingcj/IMG_3125_jbbdxv.jpg',
			alt: ''
		},
		{
			id: 2,
			imagePath:
				'https://res.cloudinary.com/dt9pi5obp/image/upload/v1692807854/walkingcj/IMG_9525_cwwivz.heic',
			alt: ''
		},
		{
			id: 3,
			imagePath:
				'https://res.cloudinary.com/dt9pi5obp/image/upload/v1692807816/walkingcj/IMG_4763_dwl945.heic',
			alt: ''
		},
		{
			id: 4,
			imagePath:
				'https://res.cloudinary.com/dt9pi5obp/image/upload/v1692807831/walkingcj/IMG_9435_ib7ywd.heic',
			alt: ''
		},
		{
			id: 5,
			imagePath:
				'https://res.cloudinary.com/dt9pi5obp/image/upload/v1692807811/walkingcj/IMG_3860_doolpz.heic',
			alt: ''
		}
	];

	let carouselIndex = 0;
	let innerWidth = 640;
	let innerHeight = 640;
	let mounted = false;

	onMount(() => {
		mounted = true;
		images.forEach((i) => {
			i.imagePath =
				transformUrl({
					url: i.imagePath,
					width: innerWidth,
					height: Math.floor(innerHeight * 0.9)
				})?.toString() || '';
		});
		setInterval(() => {
			carouselIndex = (carouselIndex + 1) % images.length;
			// console.log(carouselIndex);
		}, 5000);
	});

	const [send, recieve] = crossfade({
		duration: 2000,
		easing: quintOut
	});
</script>

<svelte:window bind:innerWidth bind:innerHeight />

<svelte:head>
	{#if mounted}
		{#each images as image}
			<link rel="preload" href={image.imagePath} as="image" />
		{/each}
	{/if}
</svelte:head>

{#if mounted}
	{#each images as image, i}
		{#if i === carouselIndex}
			<img
				class="carouselImage absolute left-0 top-0 -z-10 h-[95vh] w-screen object-cover bg-sky-900"
				src={image.imagePath}
				alt={image.alt}
				sizes="100vw"
				in:send={{ key: 'carousel' }}
				out:recieve={{ key: 'carousel' }}
			/>
		{/if}
	{/each}
{:else}
	<img
		class="carouselImage absolute left-0 top-0 -z-10 h-[95vh] w-screen object-cover bg-sky-900"
		src={'https://res.cloudinary.com/dt9pi5obp/image/upload/w_640,h_640,c_lfill,f_auto/v1692807832/walkingcj/IMG_9453_rvdvim'}
		alt={images[0].alt}
		sizes="100vw"
		in:send={{ key: 'carousel' }}
		out:recieve={{ key: 'carousel' }}
	/>
{/if}

<style>
	.carouselImage {
		filter: brightness(0.5);
	}
</style>
