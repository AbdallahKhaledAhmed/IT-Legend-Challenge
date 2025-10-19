<script>
import { MediaQuery } from "svelte/reactivity";
import CourseContent from "./CourseContent.svelte";
const small = new MediaQuery("min-width: 640px")
const medium = new MediaQuery("min-width: 768px")
const {weekTitle, weekNum, weekContent} = $props()
</script>

<div class="collapse collapse-plus bg-base-100 border-base-300 rounded md:rounded-none border md:py-7 md:px-2 my-5">
  <input type="checkbox" id="Collapse" class="md:hidden" checked={medium.current?true:false} />
  <label for="Collapse" class="collapse-title font-semibold md:hidden">{weekTitle}</label>
  <div class="collapse-content md:bg-none md:border-0 flex flex-col gap-5 ">
      <div class="hidden md:flex flex-col gap-3">
        <h3 class="text-xl font-semibold">Week {weekNum}</h3>
        <p class="opacity-65">Advanced story telling technique for writers: Personas, Characters & Plots</p>
      </div>
      <div class="divide-y border-y">
        {#each weekContent as content}
        <CourseContent {...content}/>
        {/each}
      </div>
  </div>
</div>