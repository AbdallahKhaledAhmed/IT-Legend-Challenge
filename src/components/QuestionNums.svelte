<script>
  let selected = $state(0)
  let {questions} = $props()
</script>


<ul class="menu menu-horizontal gap-3 rounded-box text-white font-semibold">
  {#each questions as question, ind}
  <li>
    <button class="btn btn-ghost btn-circle border-[#ebebeb] {selected==ind?"bg-white text-[#3f55b7]":null}" onclick={()=>{selected=ind}}>{ind+1}</button>
  </li>
  {/each}
</ul>
<main class="bg-base-200 rounded-3xl center gap-3 flex-col p-10">
    <div class="w-80 h-20 bg-white"></div>
    <div class="w-80 h-20 bg-white"></div>
    <div class="w-80 h-20 bg-white"></div>
  </main>