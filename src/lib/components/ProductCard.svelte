<script lang="ts">
	export let img: string = '';
	export let alt: string = '';
	export let title: string = '';
	export let subtitle: string | undefined;
	export let description: string = '';
	export let longDescription: string = '';
	export let icon: string = '';

	import LucideBeef from '~icons/lucide/beef';
	import GisLayerLandcover from '~icons/gis/layer-landcover';
</script>

<div
	class="zoombg relative h-96 w-full overflow-hidden text-white md:w-full"
	style={`--url: url('${img}')`}
>
	<div
		class="absolute left-0 top-0 z-40 flex h-full w-full flex-col items-center justify-center gap-2 rounded-lg bg-black bg-opacity-50 p-2 md:rounded-none"
	>
		<div class="flex flex-col items-center gap-1">
			<h2 class="text-4xl">{title}</h2>
			{#if subtitle}
				<h3 class="text-2xl">{subtitle}</h3>
			{/if}
		</div>
		<div class="flex max-w-md flex-col items-center gap-2">
			<span class="text-md text-center text-sm">{description}</span>
			<button class="flex h-full items-center gap-2 rounded-lg bg-red-700 px-2 py-2 text-lg">
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

	.zoombg:hover::before {
		transform: scale(1.1);
	}
</style>
