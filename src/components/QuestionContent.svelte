<script>
	let { question } = $props();
	let isSelected = $state(1);
</script>

<div class="bg-base-200 rounded-3xl center gap-3 flex flex-col p-10 font-semibold">
	<div class="self-start">{question.id}.</div>
	<div>
		{question.question}
	</div>
	<ul class="w-full flex flex-col gap-2">
		{#each question.options as option, ind}
			<li>
				<button
					onclick={() => (isSelected = ind)}
					class="btn h-fit w-full justify-start text-start rounded-md shadow-2xl shadow-[#5d7aff] {isSelected ===
					ind
						? 'bg-[#3f55b7] text-white'
						: null}"
					><div
						class="p-3 center pl-0 border-r {isSelected === ind
							? 'border-white [&>div]:border-white'
							: 'border-[#d3d3d3] [&>div]:border-[#5d7aff]'}"
					>
						<div class="border border-white rounded w-4 h-4 center">
							<div class={isSelected === ind ? 'w-2 h-2 rounded-full border-4' : null}></div>
						</div>
					</div>
					<div>{option}</div></button
				>
			</li>
		{/each}
	</ul>
</div>
