<script>
  const {path} = $props()
</script>

<input type="checkbox" id="my_modal_6" class="modal-toggle" />
<div class="modal" role="dialog">
  <div class="modal-box max-w-none w-full h-full rounded-none">
    <label for="my_modal_6" class="btn btn-circle w-6 h-6 absolute top-3 right-3 ">X</label>
    <iframe src={path} title="C# PDF" class="w-full h-full pt-5 overflow-auto"></iframe>
  </div>
</div>
<label for="my_modal_6" class="btn">open modal</label>