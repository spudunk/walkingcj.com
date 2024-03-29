<script lang="ts">
	import Carousel from '$lib/components/Carousel.svelte';
	import ProductCard from '$lib/components/ProductCard.svelte';
	import ReviewCard from '$lib/components/ReviewCard.svelte';
	// import FeMouse from '~icons/fe/mouse';
	import MdiPhone from '~icons/mdi/phone';
	import MdiGoogle from '~icons/mdi/google';
	import MdiFacebook from '~icons/mdi/facebook';
	import { Image } from '@unpic/svelte';
	import { data, products, reviews } from '$lib';
</script>

<!-- HERO -->
<div class="relative">
	<Carousel />
	<div class="z-10 flex h-[95vh] w-screen items-center justify-center gap-2">
		<h1
			class="custom-shadow rounded-lg px-4 py-2 text-center text-xl text-white sm:text-2xl md:text-3xl"
		>
			<span class="text-2xl font-semibold text-red-700 sm:text-4xl md:text-5xl"
				>HIGH QUALITY BEEF</span
			>
			<br />raised with a <span class="font-semibold text-red-700">high quality</span> life
		</h1>

		<!-- <FeMouse class="absolute bottom-16 mx-auto animate-bounce text-5xl text-white" /> -->
	</div>
</div>

<div class="-mt-20 flex flex-col rounded-3xl bg-white">
	<!-- ABOUT -->
	<div class="flex flex-col gap-4 rounded-t-3xl bg-neutral-200">
		<div class="grid md:grid-cols-2">
			<div class="flex flex-col justify-center gap-4 px-10 py-4 lg:text-lg">
				<h2 class="text-center text-2xl font-semibold xs:text-4xl md:text-left">About Our Ranch</h2>
				<p>
					Walking CJ Ranch is a family-owned cattle company dedicated to providing high-quality
					custom beef raised with the customers preferences. With a deep-rooted commitment to the
					humane treatment of animals, we believe that a superior quality of life for our animals
					directly translates into exceptional meat. Our animals are raised on lush pastures,
					ensuring that your dining experience remains both delicious and ethically sound. In
					addition to beef we also raise other livestock to order on a limited basis, including pork
					and lamb.
				</p>
				<p>
					In addition to our premium meat offerings, Walking CJ Ranch also leases property to assist
					landowners in utilizing their pasture effectively without the burden or risk of caring for
					cattle themselves. We understand the challenges faced by landowners who wish to maximize
					their properties while preserving their time and resources. Our goal is to create a
					cooperative network of small farmers committed to providing the highest quality meats to
					their families and our community.
				</p>
			</div>
			<div class="hidden overflow-hidden md:order-first md:block">
				<Image
					src="https://res.cloudinary.com/dt9pi5obp/image/upload/v1692807805/walkingcj/IMG_3140_zvn3ts.heic"
					alt="cattle in pasture"
					class="aspect-square h-screen w-full rounded-none object-cover object-center md:rounded-tl-3xl"
					sizes="(max-width: 767px) 0vw, 50vw"
					layout="fullWidth"
					priority
					background="auto"
				/>
			</div>
		</div>
	</div>

	<!-- Products -->
	<div class="flex flex-col gap-4 px-4 pt-4 text-center md:px-0">
		<h2 class="text-2xl font-semibold xs:text-4xl">What we do</h2>
		<div class="flex flex-col justify-center gap-9 md:flex-row md:gap-1">
			{#each products as product}
				<ProductCard {...product} />
			{/each}
		</div>
	</div>

	<!-- Credibility -->
	<div class="flex flex-col gap-4 bg-neutral-200 px-4 py-4 text-center">
		<h2 class="text-2xl font-semibold text-black xs:text-4xl">What our customers say</h2>
		<div class="flex flex-col gap-5 md:mt-4">
			<div class="flex w-full flex-col justify-center gap-5 md:flex-row">
				<ReviewCard {...reviews[0]} class="md:-rotate-6" />
				<ReviewCard {...reviews[1]} class="md:rotate-6" />
			</div>
			<div class="flex w-full flex-col justify-center gap-5 md:flex-row">
				<ReviewCard {...reviews[2]} />
			</div>
			<div class="flex flex-row justify-center gap-5">
				<a
					href={data.facebook}
					class="flex flex-col items-center gap-1 rounded-lg bg-[#4267B2] px-2 py-2 text-center font-bold text-white md:flex-row"
					target="_blank"
				>
					<MdiFacebook />
					Review us on Facebook
				</a>
				<a
					href={data.google}
					class="flex flex-col items-center gap-1 rounded-lg bg-[#b33b30] px-2 py-2 text-lg font-bold text-white md:flex-row"
					target="_blank"
				>
					<MdiGoogle />
					Review us on Google
				</a>
			</div>
		</div>
	</div>
	<!-- Contact -->
	<div class="flex flex-col gap-4 text-start" id="contact">
		<div class="grid md:grid-cols-2">
			<div
				class="flex w-full flex-col justify-center gap-4 px-10 py-4 text-center md:w-auto md:text-start lg:text-lg"
			>
				<h2 class="text-center text-2xl font-semibold xs:text-4xl md:text-left">
					Like what you see?
				</h2>
				<p>
					We prefer to talk to our customers to keep things personal and maintain accountability.
					Call now to get on our waiting list or learn more.
				</p>
				<a
					href={data.phoneLink}
					class="mt-0 flex flex-row items-center justify-center gap-2 align-middle font-poppins text-xl font-semibold text-red-700 xs:text-2xl md:justify-start"
				>
					<MdiPhone />
					{data.phone}
				</a>
			</div>
			<div class="relative h-screen overflow-hidden md:order-last">
				<div
					class="absolute left-0 top-0 flex flex-col bg-black/75 p-4 text-white md:bottom-0 md:top-auto"
				>
					<div class="flex flex-row items-center gap-2">
						<Image
							src="https://res.cloudinary.com/dt9pi5obp/image/upload/w_1000,ar_1:1,c_fill,g_auto,e_art:hokusai/v1692807834/walkingcj/IMG_9459_2_jqc8z5.heic"
							alt="rancher"
							class="aspect-square h-12 w-12 rounded-full object-cover object-center xs:h-16 xs:w-16"
							layout="fixed"
							height={48}
							width={48}
						/>
						<span class="font-semi text-xl xs:text-2xl">John Hicks</span>
					</div>
					<p>
						John is a second generation farmer on the Walking CJ Ranch property. He values strong
						integrity and stands by his word and quality guarantee. He's a father, family man, and a
						great friend to his community.
					</p>
				</div>
				<Image
					src="https://res.cloudinary.com/dt9pi5obp/image/upload/v1692807840/walkingcj/IMG_9497_n1afxh.heic"
					alt="rancher"
					class="aspect-square h-full w-full object-cover object-center"
					sizes="(max-width: 767px) 100vw, 50vw"
					layout="fullWidth"
					background="auto"
				/>
			</div>
		</div>
	</div>
</div>

<style>
	.custom-shadow {
		filter: drop-shadow(0 5px 5px black);
	}
</style>
