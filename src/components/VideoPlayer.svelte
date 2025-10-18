<script>
  import { onMount } from 'svelte';
  import videojs from 'video.js';

  let {url = "/vid.mp4", thumbnail = "/thumbnail.jpg"} = $props()
  let playing = $state(false)
  let videoElement = $state(null)
  
  onMount(async()=>{
    const player = videojs(videoElement, {controls:true, fluid: true, playbackRates: [0.5, 0.75, 1, 1.25, 1.5, 2]});
    const Button = videojs.getComponent('Button');
  })
</script>



<div class="relative">
  <!-- svelte-ignore a11y_media_has_caption -->
  <video src={url} poster={thumbnail} bind:this={videoElement} class="video-js" style:border-radius=var(--radius-lg)></video>
  <button title="Play" id="Play" class="w-full h-full top-0 absolute center rounded bg-black/40" style:display={playing?"none":null} onclick={()=>{playing=true;videoElement.play()}}>
    <div role="button" class="btn btn-circle w-20 h-20" >
      <div id="play-pause-btn" class="w-1 h-0 border-red-600 rounded-sm translate-x-[20%] border-b-[10px] border-t-[10px] border-l-[15px] border-b-transparent border-t-transparent"></div>
    </div>
  </button>
</div>


<style>
  :global(.video-js .vjs-big-play-button) {
  display: none !important;
}
</style>