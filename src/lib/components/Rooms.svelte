<script lang="ts">
	import type { SwiperContainer } from 'swiper/element/bundle';
	import { Bed, CheckCircle2, Home, Palmtree, ArrowLeft, ArrowRight } from '@lucide/svelte';
	import { onMount } from 'svelte';

	const rooms = [
		{ src: '/images/room-2person.webp', alt: 'Pokój 1' },
		{ src: '/images/room-3person.webp', alt: 'Pokój 2' },
		{ src: '/images/room-detail.webp', alt: 'Pokój 3' }
	];

	const features = [
		{
			icon: Bed,
			title: 'Pokoje 2 i 3-osobowe',
			description: 'Eleganckie, nowo urządzone pokoje dostosowane do potrzeb mieszkańców'
		},
		{
			icon: Home,
			title: '36 pokoi w 3 skrzydłach',
			description: 'Wszystkie pokoje znajdują się na parterze dla wygody mieszkańców'
		},
		{
			icon: Palmtree,
			title: 'Tarasy z widokiem',
			description: 'Każdy pokój posiada taras umożliwiający kontakt z naturą'
		}
	];

	onMount(async () => {
		const { register } = await import('swiper/element/bundle');
		register();
	});

	let swiperEl: SwiperContainer;
</script>

<section id="rooms" class="scroll-m-8 bg-gradient-to-b from-warm-green-soft to-background py-20">
	<div class="container mx-auto px-4">
		<div class="mx-auto mb-16 max-w-3xl text-center">
			<h2 class="mb-6 text-4xl font-bold text-primary md:text-5xl">Komfortowe pokoje</h2>
			<p class="text-lg text-muted-foreground">
				Wszystkie nasze pokoje są eleganckie, nowo urządzone i zaprojektowane z myślą o komforcie i
				wygodzie mieszkańców.
			</p>
		</div>

		<div class="mx-auto mb-16 max-w-6xl items-center gap-12 lg:grid lg:grid-cols-2">
			<div class="relative h-full">
				<div class="carousel-wrapper relative mb-10 w-full overflow-hidden lg:mb-0 lg:h-[600px]">
					<!-- svelte-ignore a11y_click_events_have_key_events -->
					<!-- svelte-ignore a11y_no_static_element_interactions -->
					<div class="nav-btn prev-btn" on:click={() => swiperEl?.swiper.slidePrev()}>
						<ArrowLeft class="h-4 w-4" />
					</div>

					<swiper-container
						bind:this={swiperEl}
						slides-per-view="1"
						centered-slides="true"
						space-between="20"
						allow-touch-move="true"
					>
						{#each rooms as room}
							<swiper-slide>
								<img src={room.src} alt={room.alt} class="h-auto lg:h-full" />
							</swiper-slide>
						{/each}
					</swiper-container>

					<!-- svelte-ignore a11y_click_events_have_key_events -->
					<!-- svelte-ignore a11y_no_static_element_interactions -->
					<div class="nav-btn next-btn" on:click={() => swiperEl?.swiper.slideNext()}>
						<ArrowRight class="h-4 w-4" />
					</div>
				</div>
			</div>

			<div class="space-y-8">
				<div class="space-y-6">
					{#each features as { icon: Icon, title, description }}
						<div class="flex gap-4">
							<div class="flex-shrink-0">
								<div class="flex h-12 w-12 items-center justify-center rounded-full bg-primary/10">
									<Icon class="h-6 w-6 text-primary" />
								</div>
							</div>
							<div>
								<h3 class="mb-2 text-xl font-semibold text-foreground">
									{title}
								</h3>
								<p class="text-muted-foreground">{description}</p>
							</div>
						</div>
					{/each}
				</div>

				<div class="border-t border-border pt-6">
					<h4 class="mb-4 font-semibold text-foreground">Każdy pokój wyposażony w:</h4>
					<ul class="space-y-3">
						<li class="flex items-start gap-2 text-muted-foreground">
							<CheckCircle2 class="mt-0.5 h-5 w-5 flex-shrink-0 text-primary" />
							<span>Wygodne łóżka z materacami najwyższej jakości</span>
						</li>
						<li class="flex items-start gap-2 text-muted-foreground">
							<CheckCircle2 class="mt-0.5 h-5 w-5 flex-shrink-0 text-primary" />
							<span>Prywatny taras z dostępem do zieleni</span>
						</li>
						<li class="flex items-start gap-2 text-muted-foreground">
							<CheckCircle2 class="mt-0.5 h-5 w-5 flex-shrink-0 text-primary" />
							<span>WNowoczesne meble i funkcjonalne wyposażenie</span>
						</li>
						<li class="flex items-start gap-2 text-muted-foreground">
							<CheckCircle2 class="mt-0.5 h-5 w-5 flex-shrink-0 text-primary" />
							<span>Jasne, przestronne wnętrza pełne światła</span>
						</li>
					</ul>
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	.carousel-wrapper {
		position: relative;
		flex: 1 1 60%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	swiper-container {
		width: 100%;
		height: 100%;
		border-radius: 20px;
		overflow: hidden;
		box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15);
		backface-visibility: hidden;
		transform: translateZ(0);
		will-change: transform;
	}

	swiper-slide {
		display: flex;
		justify-content: center;
		align-items: center;
		background: #fff;
	}

	swiper-slide img {
		width: 100%;
		object-fit: cover;
	}

	/* Custom arrows */
	.nav-btn {
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		z-index: 10;
		background: white;
		border-radius: 9999px;
		width: 34px;
		height: 34px;
		display: flex;
		justify-content: center;
		align-items: center;
		cursor: pointer;
		transition: background 0.2s ease;
	}

	.nav-btn:hover {
		background: hsl(35 60% 55%);
		color: white;
	}

	.prev-btn {
		left: 16px;
	}

	.next-btn {
		right: 16px;
	}

	/* Pagination styling */
	swiper-container::part(pagination-bullet) {
		background: white;
		opacity: 0.8;
	}

	swiper-container::part(pagination-bullet-active) {
		background: white;
	}
</style>
