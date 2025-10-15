<script>
  import InfoRow from "./InfoRow.svelte";
  const {data} = $props()
</script>

<div class="w-60 not-last:border-b sm:not-last:border-b-0">
  {#each data as item}
  <InfoRow {...item} />
  {/each}
</div>