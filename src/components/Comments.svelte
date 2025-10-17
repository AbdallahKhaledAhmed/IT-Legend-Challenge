<script>
  import Comment from "./Comment.svelte";

  const now = new Date();
  const date = now.toLocaleDateString("en-US", {year:"numeric", month:"short", day:"numeric"})
  const comments = [
    {name:"Mohammed", img:"https://img.daisyui.com/images/profile/demo/superperson@192.webp",date:date, commentContent:"I Love ITLegend"},
    {name:"Ali", img:"https://img.daisyui.com/images/profile/demo/batperson@192.webp",date:date, commentContent:"This is the Best Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi laboriosam facilis quibusdam esse unde, pariatur earum maiores cum laudantium eius numquam quis ab officia debitis omnis consequatur dignissimos aliquid neque I have ever seen!"},
    {name:"Hany", img:"https://img.daisyui.com/images/profile/demo/distracted1@192.webp",date:date, commentContent:"I Love Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi laboriosam facilis quibusdam esse unde, pariatur earum maiores cum laudantium eius numquam quis ab officia debitis omnis consequatur dignissimos aliquid neque!"},
  ]
</script>

<div class="flex flex-col gap-4">
  <h2 class="card-title text-3xl" id="Comments">Comments</h2>
  <div>
    {#each comments as comment}
      <Comment {...comment} />
    {/each}
  </div>

  <textarea class="textarea w-full shadow-2xl" placeholder="Write a comment"></textarea>
  <button class="btn text-white bg-[#1ab69d] px-6 font-semibold w-fit">Submit Review →</button>
</div>  