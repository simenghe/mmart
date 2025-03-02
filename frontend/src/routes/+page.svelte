<script lang="ts">
	import { onMount } from 'svelte';

	// Sample products for carousel
	const carouselItems = [
		{
			id: 1,
			title: 'Used MacBook Pro',
			price: 1499,
			image: '/api/placeholder/500/400'
		},
		{
			id: 2,
			title: 'Herman Miller Chair',
			price: 499,
			image: '/api/placeholder/500/400'
		},
		{
			id: 3,
			title: 'Samsung Monitor',
			price: 349,
			image: '/api/placeholder/500/400'
		},
		{
			id: 4,
			title: 'Logitech Mouse',
			price: 59,
			image: '/api/placeholder/500/400'
		}
	];

	// Carousel state
	let currentSlide = 0;

	// Carousel controls
	function nextSlide() {
		currentSlide = (currentSlide + 1) % carouselItems.length;
	}

	function prevSlide() {
		currentSlide = (currentSlide - 1 + carouselItems.length) % carouselItems.length;
	}

	// Auto-advance carousel
	onMount(() => {
		const interval = setInterval(() => {
			nextSlide();
		}, 5000);

		return () => clearInterval(interval);
	});
</script>

<svelte:head>
	<title>MMart - Corporate Verified Used Marketplace</title>
</svelte:head>

<main>
	<!-- Hero Section with Carousel and Map -->
	<section class="py-8">
		<div class="container mx-auto px-4">
			<h1 class="mb-6 text-center text-3xl font-bold text-indigo-900">
				MMart - Corporate Verified Used Marketplace
			</h1>
			<p class="mx-auto mb-8 max-w-3xl text-center text-lg">
				Premium used equipment from verified corporate sellers with warranty and transparent
				history.
			</p>

			<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
				<!-- Product Carousel (Left Side) -->
				<div class="overflow-hidden rounded-lg bg-white shadow-md">
					<div class="relative h-96">
						{#each carouselItems as item, i}
							<div
								class="absolute inset-0 transition-opacity duration-500"
								style="opacity: {currentSlide === i ? '1' : '0'}"
							>
								<img src={item.image} alt={item.title} class="h-full w-full object-cover" />
								<div class="absolute bottom-0 left-0 right-0 bg-black bg-opacity-50 p-4 text-white">
									<h3 class="text-xl font-semibold">{item.title}</h3>
									<p class="text-lg">${item.price}</p>
								</div>
							</div>
						{/each}

						<!-- Carousel Controls -->
						<button
							class="absolute left-2 top-1/2 -translate-y-1/2 transform rounded-full bg-black bg-opacity-50 p-2 text-white"
							on:click={prevSlide}
						>
							<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M15 19l-7-7 7-7"
								></path>
							</svg>
						</button>
						<button
							class="absolute right-2 top-1/2 -translate-y-1/2 transform rounded-full bg-black bg-opacity-50 p-2 text-white"
							on:click={nextSlide}
						>
							<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M9 5l7 7-7 7"
								></path>
							</svg>
						</button>

						<!-- Carousel Indicators -->
						<div class="absolute bottom-16 left-0 right-0 flex justify-center space-x-2">
							{#each carouselItems as _, i}
								<button
									class="h-3 w-3 rounded-full {currentSlide === i
										? 'bg-white'
										: 'bg-white bg-opacity-50'}"
									on:click={() => (currentSlide = i)}
								></button>
							{/each}
						</div>
					</div>
				</div>

				<!-- Map Component (Right Side) -->
				<div class="overflow-hidden rounded-lg bg-white shadow-md">
					<div class="relative h-96 bg-gray-100">
						<!-- Map Placeholder - In a real app, you would integrate a map library here -->
						<div class="absolute inset-0 bg-indigo-100">
							<img src="/api/placeholder/600/400" alt="Map" class="h-full w-full object-cover" />

							<!-- Sample map markers -->
							<div class="absolute left-1/4 top-1/4 -translate-x-1/2 -translate-y-1/2 transform">
								<div class="flex h-6 w-6 items-center justify-center rounded-full bg-indigo-600">
									<div class="h-4 w-4 rounded-full bg-white"></div>
								</div>
							</div>
							<div class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 transform">
								<div class="flex h-6 w-6 items-center justify-center rounded-full bg-indigo-600">
									<div class="h-4 w-4 rounded-full bg-white"></div>
								</div>
							</div>
							<div
								class="absolute bottom-1/3 right-1/4 -translate-x-1/2 -translate-y-1/2 transform"
							>
								<div class="flex h-6 w-6 items-center justify-center rounded-full bg-indigo-600">
									<div class="h-4 w-4 rounded-full bg-white"></div>
								</div>
							</div>
						</div>
						<div class="absolute bottom-4 right-4 rounded-lg bg-white p-2 shadow-md">
							<p class="text-sm text-gray-600">23 locations nationwide</p>
						</div>
					</div>
				</div>
			</div>

			<!-- Call to Action -->
			<div class="mt-10 text-center">
				<div class="flex flex-col justify-center gap-4 sm:flex-row">
					<a
						href="/browse"
						class="rounded-lg bg-indigo-600 px-6 py-3 font-semibold text-white hover:bg-indigo-700"
						>Browse Listings</a
					>
					<a
						href="/sell"
						class="rounded-lg border border-indigo-600 bg-white px-6 py-3 font-semibold text-indigo-600 hover:bg-indigo-50"
						>Become a Seller</a
					>
				</div>
			</div>
		</div>
	</section>

	<!-- Features Section -->
	<section class="bg-gray-50 py-10">
		<div class="container mx-auto px-4">
			<div class="grid grid-cols-1 gap-6 md:grid-cols-3">
				<div class="rounded-lg bg-white p-6 text-center shadow-md">
					<div
						class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-full bg-indigo-100 text-indigo-600"
					>
						<svg class="h-6 w-6" fill="currentColor" viewBox="0 0 20 20">
							<path
								fill-rule="evenodd"
								d="M6.267 3.455a3.066 3.066 0 001.745-.723 3.066 3.066 0 013.976 0 3.066 3.066 0 001.745.723 3.066 3.066 0 012.812 2.812c.051.643.304 1.254.723 1.745a3.066 3.066 0 010 3.976 3.066 3.066 0 00-.723 1.745 3.066 3.066 0 01-2.812 2.812 3.066 3.066 0 00-1.745.723 3.066 3.066 0 01-3.976 0 3.066 3.066 0 00-1.745-.723 3.066 3.066 0 01-2.812-2.812 3.066 3.066 0 00-.723-1.745 3.066 3.066 0 010-3.976 3.066 3.066 0 00.723-1.745 3.066 3.066 0 012.812-2.812zm7.44 5.252a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
								clip-rule="evenodd"
							></path>
						</svg>
					</div>
					<h3 class="mb-2 text-lg font-semibold">Verified Corporate Sellers</h3>
					<p class="text-gray-600">All equipment comes from verified businesses.</p>
				</div>
				<div class="rounded-lg bg-white p-6 text-center shadow-md">
					<div
						class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-full bg-indigo-100 text-indigo-600"
					>
						<svg class="h-6 w-6" fill="currentColor" viewBox="0 0 20 20">
							<path
								fill-rule="evenodd"
								d="M4 2a2 2 0 00-2 2v11a3 3 0 106 0V4a2 2 0 00-2-2H4zm1 14a1 1 0 100-2 1 1 0 000 2zm5-1.757l4.9-4.9a2 2 0 000-2.828L13.485 5.1a2 2 0 00-2.828 0L10 5.757v8.486zM16 18H9.071l6-6H16a2 2 0 012 2v2a2 2 0 01-2 2z"
								clip-rule="evenodd"
							></path>
						</svg>
					</div>
					<h3 class="mb-2 text-lg font-semibold">Warranty Included</h3>
					<p class="text-gray-600">90-day warranty on all purchased items.</p>
				</div>
				<div class="rounded-lg bg-white p-6 text-center shadow-md">
					<div
						class="mx-auto mb-4 flex h-12 w-12 items-center justify-center rounded-full bg-indigo-100 text-indigo-600"
					>
						<svg class="h-6 w-6" fill="currentColor" viewBox="0 0 20 20">
							<path
								fill-rule="evenodd"
								d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2v-3a1 1 0 00-1-1H9z"
								clip-rule="evenodd"
							></path>
						</svg>
					</div>
					<h3 class="mb-2 text-lg font-semibold">Full History Reports</h3>
					<p class="text-gray-600">Complete transparency on all equipment history.</p>
				</div>
			</div>
		</div>
	</section>
</main>
