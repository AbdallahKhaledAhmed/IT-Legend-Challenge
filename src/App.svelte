<script>
  import Breadcrumb from "./components/Breadcrumb.svelte";
  import Comments from "./components/Comments.svelte";
  import CourseMaterial from "./components/CourseMaterial.svelte";
  import PdfViewer from "./components/PdfViewer.svelte";
  import Quizz from "./components/Quizz.svelte";
  import Week from "./components/Week.svelte";
  import { week1_4, week5_8 } from "./components/weeks";
</script>


<Breadcrumb />
<CourseMaterial />
<Comments />
<Week weekTitle="Course Introduction" weekNum="1-4" weekContent={week1_4}/>
<Week weekTitle="JavaScript Language Basics" weekNum="5-8" weekContent={week5_8}/>
<Week weekTitle="Components & Databinding" weekNum="5-8" weekContent={week5_8}/>
<!-- <Quizz /> -->
 <PdfViewer path="/CSharp.pdf" />