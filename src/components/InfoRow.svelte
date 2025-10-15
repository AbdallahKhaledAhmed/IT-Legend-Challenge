
<script>
  const {icon, name, value} = $props()
</script>

<div class="info-row py-4 flex justify-between">
  <div class="flex justify-start items-center gap-2">
    <span class={icon} style="width: 20px; height: 20px;"></span>
    <span>{name}:</span>
  </div>
  <span>{value}</span>
</div>