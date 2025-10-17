<script>
  import Breadcrumb from "./components/Breadcrumb.svelte";
  import Navigation from "./components/Navigation.svelte";
  import Comments from "./components/Comments.svelte";
  import CourseMaterial from "./components/CourseMaterial.svelte";
  import Leaderboard from "./components/Leaderboard.svelte";
  import PdfViewer from "./components/PdfViewer.svelte";
  import Progress from "./components/Progress.svelte";
  import Quizz from "./components/Quizz.svelte";
  import Week from "./components/Week.svelte";
  import { week1_4, week5_8 } from "./components/weeks";
  import VideoPlayer from "./components/VideoPlayer.svelte";
</script>


<Breadcrumb />
<CourseMaterial />
<Comments />
<div id="Curriculm">
  <Week weekTitle="Course Introduction" weekNum="1-4" weekContent={week1_4}/>
  <Week weekTitle="JavaScript Language Basics" weekNum="5-8" weekContent={week5_8}/>
  <Week weekTitle="Components & Databinding" weekNum="5-8" weekContent={week5_8}/>
</div>
<!-- <Quizz /> -->
<PdfViewer path="/CSharp.pdf" />

<Progress  initialValue=80/>
<Leaderboard />
<Navigation />
<VideoPlayer />