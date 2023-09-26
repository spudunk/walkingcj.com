<script lang="ts">
	import Navbar from '$lib/components/Navbar.svelte';
	import { scrolled } from '$lib/stores';
	import { onMount } from 'svelte';
	import '../app.css';
	import Footer from '$lib/components/Footer.svelte';
	import '@fontsource/poppins/400.css';
	import '@fontsource/poppins/500.css';
	import '@fontsource/poppins/700.css';

	const ogImage =
		'https://res.cloudinary.com/dt9pi5obp/image/upload/c_scale,w_1200/c_crop,g_auto,h_630,w_1200/v1692807846/walkingcj/IMG_9519_fa6h52.jpg';
	onMount(() => {
		onscroll = () => {
			var scrollTop =
				window.scrollY !== undefined
					? window.scrollY
					: (document.documentElement || document.body.parentNode || document.body).scrollTop;
			scrolled.set(scrollTop > 0);
		};
	});
</script>

<svelte:head>
	<title>Walking CJ Ranch</title>

	<!-- base metadata -->
	<meta
		name="description"
		content="High quality beef in SW Washington State. We believe that a quality life makes quality meat Contact us today to join our network or waiting list."
	/>

	<!-- open graph / facebook metadata -->
	<meta property="og:url" content="https://walkingcj.com" />
	<meta property="og:type" content="website" />
	<meta property="og:title" content="Walking CJ Ranch" />
	<meta
		property="og:description"
		content="High quality beef in SW Washington State. We believe that a quality life makes quality meat Contact us today to join our network or waiting list."
	/>
	<meta property="og:image" content={ogImage} />

	<!-- twitter / x metadata -->
	<meta name="twitter:card" content="summary_large_image" />
	<meta property="twitter:domain" content="walkingcj.com" />
	<meta property="twitter:url" content="https://walkingcj.com" />
	<meta name="twitter:title" content="Walking CJ Ranch" />
	<meta
		name="twitter:description"
		content="High quality beef in SW Washington State. We believe that a quality life makes quality meat Contact us today to join our network or waiting list."
	/>
	<meta name="twitter:image" content={ogImage} />
</svelte:head>

<Navbar />
<div class="overflow-x-hidden">
	<slot />
</div>
<Footer />
