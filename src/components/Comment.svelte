<script>
	const { name, img, date, commentContent } = $props();
</script>

<article class="flex items-center justify-start not-last:border-b py-5">
	<div class="p-6 gap-4 w-fit self-start">
		<div class="avatar">
			<div class="w-21 rounded-full">
				<img src={img} alt="Student" loading="lazy" />
			</div>
		</div>
	</div>

	<div class="flex flex-col gap-2 opacity-65">
		<header class="flex flex-col gap-1">
			<b>{name}</b>
			<p class="text-sm">{date}</p>
		</header>
		<p class="text-sm">{commentContent}</p>
	</div>
</article>
