<script>
	import { getContext } from 'svelte';
	import ModalButton from './ModalButton.svelte';

	const { name, questions = '', time = '', vidind = null } = $props();
	let quizzTime = getContext('quizzTime');
	let videoIndex = getContext('videoIndex');
</script>

<ModalButton
	modalId={questions ? 'my_modal_4' : time ? 'my_modal_1' : null}
	btnClass="flex w-full cursor-pointer justify-between border-y py-3 hover:text-[#1ab69d] transition duration-300"
	click={() => {
		if (quizzTime.time === -1 && time && questions) {
			quizzTime.time = +time;
		} else if (vidind !== null) {
			videoIndex.data = vidind;
		}
	}}
>
	<div class="flex items-center gap-2 text-start">
		<span class="icon-[formkit--filedoc]" style="width: 20px; height: 20px;"></span>
		<span>{name}</span>
	</div>
	{#if questions || time}
		<div class="flex flex-wrap justify-end gap-2">
			<span class="text-sm text-emerald-800 bg-[#f2faf8] px-2 rounded"
				>{questions || 0} QUESTIONS</span
			>
			<span class="text-sm text-rose-700 bg-[#fdf2f4] px-2 rounded">{time || 0} MINUTES</span>
		</div>
	{:else}
		<span class="icon-[icon-park-outline--lock-one]" style="width: 20px; height: 20px"></span>
	{/if}
</ModalButton>
