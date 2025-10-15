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
    <div class="card shadow-2xl max-w-180">
      <div class="flex flex-col sm:flex-row justify-between items-center p-6 sm:gap-15">
        <DataCollection {data} />
        <DataCollection {data} />
      </div>
    </div>
</div>