<script>
  const {videoElement} = $props()
</script>

<div class="absolute bottom-0 left-0 w-full h-10 bg-gray-800">
  <button onclick={()=>videoElement.play()}>l</button>
</div>