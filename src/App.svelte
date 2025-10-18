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
  import Ask from "./components/Ask.svelte";
</script>

<PdfViewer path="/CSharp.pdf" />
<Ask />
<Quizz />
<Leaderboard />

<header class="px-5">
  <Breadcrumb />
  <h1>Starting SEO as your Home</h1>
</header>
<main class="flex flex-wrap p-2 md:p-5">
  <div class="w-full md:w-2/3 flex flex-col gap-5 md:pr-5 p-0">
    <VideoPlayer />
    <Navigation />
    <CourseMaterial />
    <Comments />
  </div>
  <div class="w-full md:w-1/3 flex flex-col gap-10 pl-5">
    <h2>Topics for This Course</h2>
    <Progress  initialValue=63/>
    <div id="Curriculm">
      <Week weekTitle="Course Introduction" weekNum="1-4" weekContent={week1_4}/>
      <Week weekTitle="JavaScript Language Basics" weekNum="5-8" weekContent={week5_8}/>
      <Week weekTitle="Components & Databinding" weekNum="5-8" weekContent={week5_8}/>
    </div>
  </div>
</main>




