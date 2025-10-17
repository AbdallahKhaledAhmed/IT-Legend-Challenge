<script>
  let playing = $state(false)
</script>



<div class="relative w-2/3 h-fit">
  <video src="/vid.mp4" poster="/thumbnail.jpg">
  </video>
  <div class="w-full h-full top-0 absolute bg-black/40 center">
    <button class="btn btn-circle w-20 h-20" onclick={()=>{playing=!playing}}>
      <div id="play-pause-btn" class="w-1 h-0 border-red-600 rounded-sm translate-x-[20%] border-b-[10px] border-t-[10px] border-l-[15px] border-b-transparent border-t-transparent"></div>
    </button>
  </div>
</div>