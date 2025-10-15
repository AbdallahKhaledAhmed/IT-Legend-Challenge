<script>
  const {name, img, date, commentContent} = $props()
</script>

<div class="flex items-center justify-start">
    <div class="flex flex-wrap p-6 gap-4 justify-between w-fit">
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
  </div>