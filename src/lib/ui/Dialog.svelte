<script lang="ts">
	import { Expand, X } from '@lucide/svelte';

	export let img_src = '';
	export let img_alt = 'Dialog Image';
	export let type = 'big';

	let showImage = false;
</script>

<!-- svelte-ignore a11y_mouse_events_have_key_events -->
<!-- svelte-ignore a11y_no_static_element_interactions -->
<!-- svelte-ignore a11y_click_events_have_key_events -->
<div
	class="group relative w-full cursor-pointer overflow-hidden rounded-lg shadow-lg"
	class:h-20={type === 'small'}
	class:h-64={type === 'medium'}
	class:h-80={type === 'big'}
	on:click={() => {
		showImage = true;
	}}
>
	<img
		src={img_src}
		alt={img_alt}
		class="h-full w-full object-cover transition-all duration-300 group-hover:scale-110"
	/>
	<div
		class="invisible absolute inset-0 top-0 left-0 z-50 flex h-full items-center justify-center bg-black/20 transition-all duration-100 group-hover:visible group-hover:opacity-100"
	>
		<Expand class="h-8 w-8 text-white" />
	</div>
</div>

<!-- svelte-ignore a11y_click_events_have_key_events -->
<!-- svelte-ignore a11y_no_static_element_interactions -->
{#if showImage}
	<div
		class="fixed inset-0 z-50 flex items-center justify-center bg-black/70 p-4"
		on:click={() => {
			showImage = false;
		}}
	>
		<div class="relative max-h-full max-w-full overflow-auto rounded-lg bg-white p-4 shadow-lg">
			<img src={img_src} alt={img_alt} class="max-h-[80vh] max-w-[80vw] object-contain" />
			<button
				class="absolute top-2 right-2 rounded-full border-2 border-green-800 bg-white p-1 shadow hover:bg-gray-100"
				on:click={() => {
					showImage = false;
				}}
			>
				<X class="h-6 w-6 text-gray-700 hover:text-gray-900" />
			</button>
		</div>
	</div>
{/if}
