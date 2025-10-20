<script lang="ts">
	const { modalId, btnClass = null, title = null, click = null, children = null } = $props();

	// Function to open the modal by directly checking the input
	function openModal() {
		const checkbox = document.getElementById(modalId) as HTMLInputElement;
		if (checkbox) {
			checkbox.checked = true;
		}
		if (typeof click === 'function') {
			click();
		}
	}
</script>

<button class={btnClass} {title} onclick={openModal}>{@render children?.()}</button>
