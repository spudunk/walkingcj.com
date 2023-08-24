<script lang="ts">
	import { createDialog, melt } from '@melt-ui/svelte';
	import { fade, scale } from 'svelte/transition';
	import { transformUrl } from 'unpic';

	import LucideBeef from '~icons/lucide/beef';
	import GisLayerLandcover from '~icons/gis/layer-landcover';
	import MdiClose from '~icons/mdi/close';
	import MdiPhone from '~icons/mdi/phone';

	let productTitle: string = '';
	let productDescription: string = '';
	export let img: string = '';
	// export let alt: string = '';
	export let subtitle: string | undefined;
	export let longDescription: string = '';
	export let icon: string = '';
	export { productTitle as title, productDescription as description };

	const {
		elements: { trigger, overlay, content, title, description, close, portalled },
		states: { open }
	} = createDialog();

	let innerWidth = 640;

	$: url = transformUrl({
		url: img,
		width: innerWidth >= 768 ? innerWidth / 2 : innerWidth,
		height: 384,
	});

</script>

<svelte:window bind:innerWidth />

<div
	class="zoombg relative h-96 w-full overflow-hidden text-white"
	style={`--url: url('${url}')`}
>
	<div
		class="absolute left-0 top-0 z-40 flex h-full w-full flex-col items-center justify-center gap-2 rounded-lg bg-black bg-opacity-50 p-2 md:rounded-none"
	>
		<div class="flex flex-col items-center gap-1">
			<h2 class="text-2xl xs:text-4xl">{productTitle}</h2>
			{#if subtitle}
				<h3 class="text-xl xs:text-2xl">{subtitle}</h3>
			{/if}
		</div>
		<div class="flex max-w-md flex-col items-center gap-2">
			<span class="text-md text-center text-sm">{productDescription}</span>
			<button
				use:melt={$trigger}
				class="flex h-full items-center gap-2 rounded-lg bg-red-700 px-2 py-2 text-lg transition-colors hover:bg-red-600"
			>
				{#if icon == 'beef'}
					<LucideBeef />
				{:else if icon == 'location'}
					<GisLayerLandcover />
				{/if}
				Learn More
			</button>
		</div>
	</div>
</div>

<div use:melt={$portalled}>
	{#if $open}
		<div use:melt={$overlay} class="fixed inset-0 z-50 bg-black/50" />
		<div
			use:melt={$content}
			transition:scale
			class="fixed left-0 top-0 z-[100] flex max-h-full w-screen flex-col gap-4 overflow-y-scroll rounded-lg bg-white p-6 shadow-lg md:left-1/2 md:top-1/2 md:max-h-[85vh] md:w-[90vw] md:max-w-[450px] md:-translate-x-1/2 md:-translate-y-1/2"
		>
			<div>
				<h2 use:melt={$title} class="m-0 text-lg font-medium text-black">
					{productTitle}
				</h2>
				<p use:melt={$description} class="mb-5 mt-2 leading-normal text-zinc-600">
					{productDescription}
				</p>
			</div>
			<div class="flex h-full flex-col gap-4">
				<p>{longDescription}</p>
				<div class="flex flex-row justify-center">
					<a
						class="hidden h-full items-center gap-2 rounded-lg bg-red-700 px-2 py-2 text-lg text-white transition-colors hover:bg-red-600 md:flex"
						href="#contact"
					>
						<MdiPhone />
						Contact Us
					</a>
					<!-- mobile -->
					<a
						class="flex h-full items-center gap-2 rounded-lg bg-red-700 px-2 py-1 text-lg text-white transition-colors hover:bg-red-600 md:hidden"
						href="tel:3602695572"
					>
						<MdiPhone />
						Call Us
					</a>
				</div>
			</div>

			<button
				use:melt={$close}
				aria-label="close"
				class="absolute right-4 top-4 inline-flex h-6 w-6 items-center justify-center rounded-full text-lg hover:bg-slate-200"
			>
				<MdiClose />
			</button>
		</div>
	{/if}
</div>

<style>
	.zoombg::before {
		content: '';
		position: absolute;
		/* padding-top: 100%; */
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-image: var(--url);
		background-position: center;
		background-size: cover;
		transition: transform 0.3s ease;
		transform-origin: center;
		z-index: 39;
	}

	@media (max-width: 640px) {
	}

	.zoombg:hover::before {
		transform: scale(1.1);
	}
</style>
