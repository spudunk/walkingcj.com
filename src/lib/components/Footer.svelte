<script>
	import Logo from './Logo.svelte';
	import MdiPhone from '~icons/mdi/phone';
	import MdiGoogleMaps from '~icons/mdi/google-maps';
	import MdiEmail from '~icons/mdi/email';
	import MdiFacebook from '~icons/mdi/facebook';
	import MdiGoogle from '~icons/mdi/google';
	import { data } from '$lib';
</script>

<footer class="bg-red-700 px-4 py-4">
	<div
		class="mx-auto flex w-full flex-col justify-between gap-3 font-semibold text-white md:flex-row"
	>
		<div class="flex flex-row gap-4 text-xl text-white">
			<a
				href={data.phoneLink}
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
				aria-label="telephone"
			>
				<MdiPhone />
			</a>
			<a
				href={data.maps}
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
				aria-label="location"
			>
				<MdiGoogleMaps />
			</a>
			<a
				href={data.emailLink}
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
				aria-label="email"
			>
				<MdiEmail />
			</a>
			<a
				href={data.facebook}
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
				aria-label="Facebook"
			>
				<MdiFacebook />
			</a>
			<a
				href={data.google}
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
				aria-label="Google Business"
			>
				<MdiGoogle />
			</a>
		</div>
		<div class="flex flex-row items-center gap-5">
			<Logo class="drop-shadow-2xl transition-colors" />
			<span class="block">© 2023 Walking CJ Ranch</span>
		</div>
	</div>
</footer>
