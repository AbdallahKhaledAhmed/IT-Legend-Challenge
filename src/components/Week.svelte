<script>
import { MediaQuery } from "svelte/reactivity";
import CourseContent from "./CourseContent.svelte";
const small = new MediaQuery("min-width: 640px")
const {weekTitle, weekNum, weekContent} = $props()
</script>

<div class="collapse collapse-plus bg-base-100 border-base-300 rounded sm:rounded-none border sm:py-7 sm:px-2 sm:w-1/3">
  <input type="checkbox" id="Collapse" class="sm:hidden" checked={small.current?true:false} />
  <label for="Collapse" class="collapse-title font-semibold sm:hidden">{weekTitle}</label>
  <div class="collapse-content sm:bg-none sm:border-0 flex flex-col gap-5 ">
      <div class="hidden sm:flex flex-col gap-3">
        <h3 class="text-xl font-semibold">Week {weekNum}</h3>
        <p>Advanced story telling technique for writers: Personas, Characters & Plots</p>
      </div>
      <div class="divide-y border-y">
        {#each weekContent as content}
        <CourseContent {...content}/>
        {/each}
      </div>
  </div>
</div>