<script lang="ts">
	import { X } from '@lucide/svelte';

	const images = [
		{
			src: '/images/room-2person.webp',
			alt: 'Pokój 2-osobowy z dostępem do ogrodu',
			category: 'Budynek'
		},
		{
			src: '/images/room-3person-new.webp',
			alt: 'Przestronny pokój 3-osobowy',
			category: 'Pokoje'
		},
		{ src: '/images/room-2beds-blue.webp', alt: 'Elegancki pokój 2-osobowy', category: 'Pokoje' },
		{ src: '/images/room-window-view.webp', alt: 'Pokój z widokiem na zieleń', category: 'Pokoje' },
		{ src: '/images/room-care-beds.webp', alt: 'Pokój z łóżkami medycznymi', category: 'Pokoje' },
		{ src: '/images/room-care-beds.webp', alt: 'Pokój z łóżkami medycznymi', category: 'Pokoje' },
		{ src: '/images/room-bathroom.webp', alt: 'Dostosowana łazienka', category: 'Łazienki' },
		{ src: '/images/room-care-beds.webp', alt: 'Pokój z łóżkami medycznymi', category: 'Pokoje' },
		{ src: '/images/gallery-bed-detail.webp', alt: 'Komfortowe wyposażenie', category: 'Pokoje' }
	];

	let img = false;
	let imgSrc = '';

	const showimg = (src: string) => {
		console.log(src);
		imgSrc = src;
		img = true;
	};
</script>

<div class="min-h-screen">
	<section class="bg-gradient-to-b from-warm-green-subtle to-background pt-32 pb-16">
		<div class="container mx-auto px-4">
			<div class="mx-auto max-w-3xl text-center">
				<h1 class="mb-6 text-4xl font-bold text-primary md:text-5xl">Galeria</h1>
				<p class="text-lg text-muted-foreground">
					Zapraszamy do obejrzenia naszego ośrodka. Zobacz komfortowe pokoje, nowoczesne wyposażenie
					i piękne otoczenie.
				</p>
			</div>
		</div>
	</section>

	<section class="py-16">
		<div class="container mx-auto px-4">
			<div class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3">
				<!-- svelte-ignore a11y_click_events_have_key_events -->
				<!-- svelte-ignore a11y_no_static_element_interactions -->
				{#each images as image}
					<!-- svelte-ignore a11y_click_events_have_key_events -->
					<div
						class="group relative aspect-[4/3] cursor-pointer overflow-hidden rounded-xl bg-muted"
					>
						<img
							src={image.src}
							alt={image.alt}
							class="h-full w-full object-cover transition-transform duration-300 group-hover:scale-110"
						/>
						<div
							class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 transition-opacity duration-300 group-hover:opacity-100"
							on:click={() => {
								console.log(image.src);
								showimg(image.src);
							}}
						>
							<div class="absolute right-0 bottom-0 left-0 p-4 text-white">
								<p class="text-sm font-medium">{image.category}</p>
								<p class="text-xs text-white/80">{image.alt}</p>
							</div>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</section>
</div>

{#if img}
	<div class="fixed inset-0 z-40 mt-10 flex items-center justify-center bg-black/70 p-4">
		<div class="relative max-h-full max-w-full overflow-auto rounded-lg bg-white p-4 shadow-lg">
			<button
				class="absolute top-2 right-2 z-40 rounded-full bg-white p-2 text-gray-700 hover:bg-gray-200"
				on:click={() => (img = false)}
			>
				<X class="h-6 w-6" />
			</button>
			<img src={imgSrc} alt="Powiększony obrazek" class="max-h-[80vh] w-auto rounded" />
		</div>
	</div>
{/if}
