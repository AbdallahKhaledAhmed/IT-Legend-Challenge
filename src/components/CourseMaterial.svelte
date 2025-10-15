<script>
  import DataCollection from "./DataCollection.svelte";


  const data = [
    {icon:`icon-[iconamoon--clock-light]`,name:"Duration",value:"3 weeks"},
    {icon:`icon-[tabler--books]`,name:"Lessons",value:"8"},
    {icon:`icon-[streamline-freehand--newspaper-read-man]`,name:"Enrolled",value:"65 Students"},
    {icon:`icon-[iconoir--language]`,name:"Language",value:"English"},
    ]
</script>

<div class="flex flex-col gap-4">
  <h2 class="card-title text-3xl">Course Materials</h2>
    <div class="card bg-base-100 card-xl shadow-2xl w-fit">
      <div class="flex flex-wrap p-6 gap-4 justify-between w-70 lg:w-150">
          <DataCollection {data} />
          <DataCollection {data} />
      </div>
    </div>
</div>

<style>
  :global(.info-row:not(:last-child)) {
  border-bottom: 1px solid;
}
</style>