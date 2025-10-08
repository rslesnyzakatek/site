<script>
	import { Heart } from '@lucide/svelte';
	import logo from '$lib/assets/logo-light.svg';
</script>

<footer class="bg-primary py-12 text-primary-foreground">
	<div class="container mx-auto px-4">
		<div class="mb-8 grid gap-8 md:grid-cols-3">
			<div>
				<div class="h-14">
					<img src={logo} alt="Leśny Zakątek" class="h-full w-auto" />
				</div>
				<p class="leading-relaxed text-primary-foreground/80">
					Rezydencja Seniora w sercu przyrody. Profesjonalna opieka i ciepła atmosfera dla Twoich
					bliskich.
				</p>
			</div>

			<div>
				<h4 class="mb-4 text-lg font-semibold">Kontakt</h4>
				<div class="space-y-2 text-primary-foreground/80">
					<p>Olchowo 101 72-200 Nowogard</p>
					<p>woj. zachodniopomorskie</p>
					<p>Tel: +48 797 187 786</p>
					<p>Email: lesnyzakatek.nowogard@gmail.com</p>
				</div>
			</div>

			<div>
				<h4 class="mb-4 text-lg font-semibold">Godziny</h4>
				<div class="space-y-2 text-primary-foreground/80">
					<p>Biuro: 8:00 - 20:00</p>
					<p>Odwiedziny: Codziennie</p>
					<p class="pt-2">Opieka całodobowa</p>
				</div>
			</div>
		</div>

		<div class="border-t border-primary-foreground/20 pt-8 text-center">
			<div
				class="flex flex-col items-center justify-center gap-2 text-primary-foreground/70 md:flex-row"
			>
				<p>© 2025 Rezydencja Seniora Leśny Zakątek.</p>
				<p class="text-sm font-light">
					Stworzone z <Heart class="inline h-4 w-4 fill-accent text-accent" /> dla seniorów.
				</p>
			</div>
		</div>
	</div>
</footer>
