<script>
  import InfoRow from "./InfoRow.svelte";
  const {data} = $props()
</script>

<div class="w-60">
            {#each data as item}
            <InfoRow {...item} />
            {/each}
</div>