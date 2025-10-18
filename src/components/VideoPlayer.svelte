<script>
  import VideoControls from "./VideoControls.svelte";

  let {url = "/vid.mp4", thumbnail = "/thumbnail.jpg"} = $props()
  let playing = $state(false)
  let videoElement = $state(null)
  
  $effect(()=>{
    if(playing) {
      videoElement.play()
    }else {
      videoElement.pause()
    }
  })
</script>



<div class="relative">
  <!-- svelte-ignore a11y_media_has_caption -->
  <video src={url} poster={thumbnail} bind:this={videoElement} class="rounded"></video>
  <button title={playing?"Pause":"Play"} id="Play/Pause" class="w-full h-full top-0 absolute center rounded {playing?"bg-transparent":"bg-black/40"}" onclick={()=>{playing=!playing}}>
    <div role="button" class="btn btn-circle w-20 h-20 {playing?"hidden":null}" >
      <div id="play-pause-btn" class="w-1 h-0 border-red-600 rounded-sm translate-x-[20%] border-b-[10px] border-t-[10px] border-l-[15px] border-b-transparent border-t-transparent"></div>
    </div>
  </button>
</div>