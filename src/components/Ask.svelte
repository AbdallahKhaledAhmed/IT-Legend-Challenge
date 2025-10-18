<script>
  let questionContent = $state("")
</script>

<input type="checkbox" id="my_modal_3" class="modal-toggle" />
<div class="modal" role="dialog">
  <main class="modal-box max-w-none w-full h-full rounded-none flex justify-center items-start flex-col gap-4">
    <label for="my_modal_3" class="btn btn-circle w-6 h-6 absolute top-3 right-3 ">X</label>
    <textarea class="textarea w-full shadow-2xl h-[50%]" placeholder="Write a question" bind:value={questionContent}></textarea>
    <!-- svelte-ignore a11y_click_events_have_key_events -->
    <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
    <label for="my_modal_3" class="btn text-white bg-[#1ab69d] px-6 font-semibold w-fit {questionContent.length===0?"opacity-50":null}" style:pointer-events={questionContent.length===0?"none":null} onclick={()=>questionContent=""}>Submit Question →</label>
  </main>
</div>