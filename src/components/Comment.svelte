<script>
  const {name, img, date, commentContent} = $props()
</script>

<article class="flex items-center justify-start not-last:border-b">
  <div class="p-6 gap-4 w-fit self-start">
    <div class="avatar">
      <div class="w-24 rounded-full">
        <img src={img} alt="Student" loading="lazy" />
      </div>
    </div>
  </div>

  <div class="flex flex-col">
    <header>
      <b>{name}</b>
      <p>{date}</p>
    </header>
    <p>{commentContent}</p>
  </div>
</article>