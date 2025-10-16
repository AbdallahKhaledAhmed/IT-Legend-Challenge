<script>
 const {name, questions="", time=""} = $props()
</script>

<div class="flex justify-between border-y">
  <div class="flex items-center">
    <span class="icon-[formkit--filedoc]" style="width: 20px; height: 20px;"></span>
    <span>{name}</span>
  </div>
  {#if questions||time}
    <div class="flex flex-wrap justify-end gap-2">
      <span class="text-sm text-[#60bba9] bg-[#f2faf8] px-2 rounded">{questions||0} QUESTIONS</span>
      <span class="text-sm text-[#e55762] bg-[#fdf2f4]">{time||0} MINUTES</span>
    </div>
  {:else}
    <span class="icon-[icon-park-outline--lock-one]" style="width: 20px; height: 20px; color: #000;"></span>
  {/if}
</div>