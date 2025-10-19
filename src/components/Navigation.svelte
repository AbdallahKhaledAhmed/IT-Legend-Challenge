<script>
  import ModalButton from "./ModalButton.svelte";

</script>



<ul class="menu menu-horizontal gap-3 rounded-box [&>li>*]:border-[#bebdbd] opacity-80">
  <li><a title="Comments" class="btn btn-ghost btn-circle" href="#Comments"><span class="icon-[mdi--comment-text-outline]" style="width: 24px; height: 24px;"></span></a></li>
  <li><a title="Curriculm" class="btn btn-ghost btn-circle" href="#Curriculm"><span class="icon-[qlementine-icons--book-16]" style="width: 24px; height: 24px;"></span></a></li>
  <li><ModalButton title="Leaderboard" modalId="my_modal_2" btnClass="btn btn-ghost btn-circle"><span class="icon-[solar--cup-star-linear]" style="width: 24px; height: 24px;"></span></ModalButton></li>
  <li><ModalButton title="Ask Question" modalId="my_modal_3" btnClass="btn btn-ghost btn-circle"><span class="icon-[akar-icons--chat-question]" style="width: 24px; height: 24px;"></span></ModalButton></li>
  <li><ModalButton modalId="my_modal_4" btnClass="btn btn-ghost btn-circle">open modal</ModalButton></li>
</ul>
