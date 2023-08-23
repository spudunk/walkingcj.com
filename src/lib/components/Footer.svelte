<script>
	import Logo from './Logo.svelte';
	import MdiPhone from '~icons/mdi/phone';
	import MdiGoogleMaps from '~icons/mdi/google-maps';
	import MdiEmail from '~icons/mdi/email';
	import MdiFacebook from '~icons/mdi/facebook';
	import MdiGoogle from '~icons/mdi/google';
</script>

<footer class="bg-red-700 py-4 px-4">
	<div class="container mx-auto flex w-full flex-row justify-between font-semibold text-white">
		<div class="flex flex-row gap-4 text-xl text-white">
			<a
				href="tel:3602695572"
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
			>
				<MdiPhone />
			</a>
			<a
				href="https://goo.gl/maps/dkBbgkKH2CB9FaQMA"
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
			>
				<MdiGoogleMaps />
			</a>
			<a
				href="mailto:john@walkingcj.com"
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
			>
				<MdiEmail />
			</a>
			<a
				href="https://www.facebook.com/groups/walkingcjranch/"
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
			>
				<MdiFacebook />
			</a>
			<a
				href="https://example.com"
				class="flex flex-row items-center gap-2 align-middle transition-colors hover:text-slate-300"
			>
				<MdiGoogle />
			</a>
		</div>
		<div class="flex flex-row items-center gap-5">
			<Logo class="drop-shadow-2xl transition-colors" />
			<span class="hidden md:block">© 2023 Walking CJ Ranch</span>
		</div>
	</div>
</footer>
