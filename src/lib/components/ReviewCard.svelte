<script lang="ts">
	export let name: string;
	export let review: string;
	export let img: string;

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
	class={`relative flex w-full flex-row rounded-lg border-2 border-gray-300 bg-white md:w-1/2 lg:w-1/3 ${$$props.class}`}
>
	<div
		class="bg flex h-full w-1/3 rounded-lg md:aspect-square"
		style={`--url: url('${img}')`}
	></div>
	<div class="flex w-2/3 flex-col justify-between p-2 text-start">
		<div class="flex w-full flex-row justify-between">
			<span class="text-xl font-semibold">{name}</span>
			<MdiFacebookMessenger class="text-xl text-slate-300" />
		</div>
		<span class="whitespace-pre-wrap">{review}</span>
	</div>
</div>

<style>
	.bg::before {
		content: '';
		position: absolute;
		/* padding-top: 100%; */
		top: 0;
		left: 0;
		width: 33.33333333%;
		height: 100%;
		background-image: var(--url);
		background-position: center;
		background-size: cover;
		transition: transform 0.3s ease;
		transform-origin: center;
		z-index: 1;
		border-radius: 0.5rem;
	}
</style>
