<script>
	let { initialValue } = $props();
	let value = $state(0);
	let progressElement = $state(null);

	$effect(() => {
		if (!progressElement) return;
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						value = initialValue;
						observer.disconnect();
					}
				});
			},
			{ threshold: 0.1 }
		);
		observer.observe(progressElement);
		return () => observer.disconnect();
	});
</script>

<div id="progress-label" class="hidden">Your Course Progress</div>

<div
	class="[&_*]:border-[#bebdbd] progress-bar rounded h-2 w-full bg-base-300 flex justify-start"
	role="progressbar"
	aria-labelledby="progress-label"
	aria-valuenow={value}
	aria-valuemin="0"
	aria-valuemax="100"
>
	<div
		bind:this={progressElement}
		class="bg-emerald-500 h-full rounded relative progress-after text-xs text-blue-700 duration-1000 ease-out"
		style:width={value + '%'}
		data-width="{value}%"
	>
		<div class="center flex-col gap-0.5 absolute right-0 translate-x-[40%] bottom-3">
			<div>
				<div class="center w-7 h-7 relative rounded-full border-[1.5px]" title="Your Progress">
					You
				</div>
			</div>
			<div
				class="w-0 h-0 border-l-[4px] border-r-[4px] border-t-[6px] !border-l-transparent !border-r-transparent"
			></div>
		</div>
	</div>
</div>
