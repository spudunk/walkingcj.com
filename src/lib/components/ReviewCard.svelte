<script lang="ts">
	import { Image } from '@unpic/svelte';
	export let name: string;
	export let review: string;
	export let img: string;
	export let alt: string;

	import MdiFacebookMessenger from '~icons/mdi/facebook-messenger';
</script>

<!-- <div>
	{#if img}
		<img src={img} alt="" />
	{/if}
	{review}
	<p>
		- {name}
	</p>
</div> -->

<div
	class={`relative grid w-full grid-cols-3 flex-row rounded-lg border-2 border-gray-300 bg-white md:w-1/2 lg:w-1/3 ${$$props.class}`}
>
	<Image
		src={img}
		layout="fixed"
		class="flex h-full w-1/3 rounded-lg md:aspect-square"
		width={144}
		height={144}
		{alt}
	/>

	<div class="col-start-2 col-end-4 flex w-full flex-col justify-between p-2 text-start">
		<div class="flex w-full flex-row justify-between">
			<span class="text-xl font-semibold">{name}</span>
			<MdiFacebookMessenger class="text-xl text-slate-300" />
		</div>
		<span class="whitespace-pre-wrap">{review}</span>
	</div>
</div>

