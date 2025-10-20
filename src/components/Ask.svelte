<script>
	let questionContent = $state('');
	let check = $state(null);
</script>

<input type="checkbox" bind:this={check} id="my_modal_3" class="modal-toggle" />
<div class="modal" role="dialog">
	<main
		class="modal-box max-w-none w-full h-full rounded-none flex justify-center items-start flex-col gap-4"
	>
		<label for="my_modal_3" class="btn btn-circle w-6 h-6 absolute top-3 right-3">X</label>
		<textarea
			class="textarea w-full shadow-2xl h-[50%] resize-none"
			placeholder="Write a question"
			bind:value={questionContent}
		></textarea>

		<button
			class="btn text-white bg-[#1ab69d] px-6 font-semibold w-fit disabled:opacity-50"
			disabled={questionContent.length === 0}
			onclick={() => {
				check.checked = false;
				questionContent = '';
			}}>Submit Question →</button
		>
	</main>
</div>
