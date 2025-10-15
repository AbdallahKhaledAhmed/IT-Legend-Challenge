<script>
import { MediaQuery } from "svelte/reactivity";
const small = new MediaQuery("min-width: 640px")
const {weekNum} = $props()
</script>

<div class="collapse collapse-plus bg-base-100 border-base-300 border">
  <input type="checkbox" class="sm:hidden" checked={small.current?true:false} />
  <div class="collapse-title font-semibold sm:hidden">How do I create an account?</div>
  <div class="collapse-content">
    <div class="border">
      <div class="hidden sm:block">
        <h3 class="text-xl font-semibold">Week {weekNum}</h3>
        <p>Advanced story telling technique for writers: Personas, Characters & Plots</p>
      </div>
      
    </div>
  </div>
</div>