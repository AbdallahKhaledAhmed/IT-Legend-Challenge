<script>
	let { questions, currentQuestion } = $props();
</script>

<ul class="menu menu-horizontal gap-3 rounded-box text-white font-semibold">
	{#each questions as _, ind}
		<li>
			<button
				class="btn btn-ghost btn-circle border-[#ebebeb] {currentQuestion.currentQuestion ===
				ind + 1
					? 'bg-white text-[#3f55b7]'
					: null}"
				onclick={() => {
					currentQuestion.currentQuestion = ind + 1;
				}}>{ind + 1}</button
			>
		</li>
	{/each}
</ul>
