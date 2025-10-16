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
 
  <div class="rounded h-2 w-100 bg-neutral-300 flex justify-start" role="progressbar">
    <div bind:this={progressElement} class="bg-emerald-500 h-full rounded relative progress-after text-xs text-blue-700 duration-1000 ease-out" style:width={value+"%"} data-width="{value}%">
      <div class="center flex-col absolute right-0 translate-x-[50%] bottom-5">
        <div class="center w-6 h-6 relative rounded-full border-2 border-gray-300 dark:border-gray-500 animate-pulse">
          You
        </div>
        <div class="w-0 h-0 border-l-[6px] border-r-[6px] border-t-[8px] border-l-transparent border-r-transparent border-t-gray-300 dark:border-t-gray-500 -mt-1 absolute -bottom-3"></div>
      </div>
    </div>
  </div>



  