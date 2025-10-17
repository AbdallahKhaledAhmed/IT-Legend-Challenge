<script>
  let {initialValue} = $props()
  let value = $state(0)
  let progressElement = $state(null)

  $effect(()=>{
    if(!progressElement) return
    const observer = new IntersectionObserver((entries)=>{entries.forEach((entry)=>{if(entry.isIntersecting){value=initialValue; observer.disconnect()}})},{threshold: 0.1})
    observer.observe(progressElement)
    return ()=> observer.disconnect()
  })
</script>
 
  <div class="[&_*]:border-[#bebdbd] progress-bar rounded h-2 w-100 bg-base-300 flex justify-start" role="progressbar">
    <div bind:this={progressElement} class="bg-emerald-500 h-full rounded relative progress-after text-xs text-blue-700 duration-1000 ease-out" style:width={value+"%"} data-width="{value}%">
      <div class="center flex-col gap-0.5 absolute right-0 translate-x-[40%] bottom-3">
        <div>
          <div class="center w-7 h-7 relative rounded-full border-[1.5px] animate-pulse">
            You
          </div>
        </div>
        <div class="w-0 h-0 border-l-[4px] border-r-[4px] border-t-[6px] !border-l-transparent !border-r-transparent"></div>
      </div>
    </div>
  </div>
