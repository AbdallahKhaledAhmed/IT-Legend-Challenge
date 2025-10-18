<script>
  import Comment from "./Comment.svelte";

  const now = new Date();
  const date = now.toLocaleDateString("en-US", {year:"numeric", month:"short", day:"numeric"})

  let comments = $state([
    {name:"Mohammed", img:"https://img.daisyui.com/images/profile/demo/superperson@192.webp",date:date, commentContent:"I Love ITLegend"},
    {name:"Ali", img:"https://img.daisyui.com/images/profile/demo/batperson@192.webp",date:date, commentContent:"This is the Best Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi laboriosam facilis quibusdam esse unde, pariatur earum maiores cum laudantium eius numquam quis ab officia debitis omnis consequatur dignissimos aliquid neque I have ever seen!"},
    {name:"Hany", img:"https://img.daisyui.com/images/profile/demo/distracted1@192.webp",date:date, commentContent:"I Love Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi laboriosam facilis quibusdam esse unde, pariatur earum maiores cum laudantium eius numquam quis ab officia debitis omnis consequatur dignissimos aliquid neque!"},
  ])

  let commentContent = $state("")
  function addComment() {
    comments.push({name:"Hany", img:"https://img.daisyui.com/images/profile/demo/distracted1@192.webp",date:date, commentContent:commentContent})
    commentContent=""
  }
</script>

<div class="flex flex-col gap-4">
  <h2 class="card-title text-3xl" id="Comments">Comments</h2>
  <div>
    {#each comments as comment}
      <Comment {...comment} />
    {/each}
  </div>

  <textarea class="textarea w-full shadow-2xl" placeholder="Write a comment" bind:value={commentContent}></textarea>
  <button class="btn text-white bg-[#1ab69d] px-6 font-semibold w-fit disabled:opacity-50" disabled={commentContent.length===0} onclick={addComment}>Submit Review →</button>
</div>  