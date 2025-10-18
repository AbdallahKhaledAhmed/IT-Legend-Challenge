<script>
  let {time} = $props()
  let mins = $state(+time)
  let secs = $state(0)

  $effect(()=>{
    const countdown = setInterval(() => {
      if(secs==0 && mins==0) return
      if(secs === 0) {
        secs = 60
        mins--
        }
      secs--
    }, 1000);
  return ()=>{clearInterval(countdown)}
  })
</script>

<div class="center w-fit gap-2 rounded px-4 py-2 bg-[#fbd500] text-white shadow-[0_0_60px_rgba(250,204,21,0.8),0_0_100px_rgba(250,204,21,0.6),0_20px_80px_rgba(250,204,21,0.5)]">
  <span class="icon-[mage--alarm-clock]" style="width: 25px; height: 25px;"></span>
  <span class="countdown font-mono text-2xl">
    <span style="--value:{mins};" aria-live="polite" aria-label={mins.toString()}>{mins}</span>:
    <span style="--value:{secs};" aria-live="polite" aria-label={secs.toString()}>{secs}</span>
  </span>
</div>