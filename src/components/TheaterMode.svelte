<script>
	import { getContext } from 'svelte';
	import { MediaQuery } from 'svelte/reactivity';

	const underMedium = new MediaQuery('max-width: 768px');
	let theaterMode = getContext('theaterMode');
</script>

<button
	title="Theater Mode"
	class="btn btn-circle bg-black/40 hover:bg-black top-5 right-5 z-10 {underMedium.current
		? 'hidden'
		: 'absolute'}"
	onclick={() => (theaterMode.status = !theaterMode.status)}
>
	<div class="h-4 w-6 border-2 border-white"></div>
</button>
