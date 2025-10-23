<script>
	import Breadcrumb from './components/Breadcrumb.svelte';
	import Navigation from './components/Navigation.svelte';
	import Comments from './components/Comments.svelte';
	import CourseMaterial from './components/CourseMaterial.svelte';
	import Leaderboard from './components/Leaderboard.svelte';
	import PdfViewer from './components/PdfViewer.svelte';
	import Progress from './components/Progress.svelte';
	import Quizz from './components/Quizz.svelte';
	import Week from './components/Week.svelte';
	import { week1_4, week5_8 } from './components/weeks';
	import VideoPlayer from './components/VideoPlayer.svelte';
	import Ask from './components/Ask.svelte';
	import { setContext } from 'svelte';
	import { MediaQuery } from 'svelte/reactivity';
	import ThemeController from './components/ThemeController.svelte';
	const underMedium = new MediaQuery('max-width: 768px');
	const videoData = [
		{ vidPath: 'vid1(720).mp4', thumbPath: 'thumbnail.webp' },
		{ vidPath: 'vid2(720).mp4', thumbPath: 'thumbnail2.webp' }
	];

	let videoIndex = $state(0);
	let quizzTime = $state(-1);
	let theaterMode = $state(true);
	let theaterStatus = $derived.by(() => (underMedium.current ? false : theaterMode));
	setContext('theaterMode', {
		get status() {
			return theaterMode;
		},
		set status(val) {
			theaterMode = val;
		}
	});
	setContext('quizzTime', {
		get time() {
			return quizzTime;
		},
		set time(val) {
			quizzTime = val;
		}
	});
	setContext('videoIndex', {
		get data() {
			return videoIndex;
		},
		set data(val) {
			videoIndex = val;
		}
	});
	let isQuizzOpen = $state(false);
</script>

<Quizz />
<PdfViewer path="CSharp.pdf" />
<Ask />
<Leaderboard />

<header class="px-5 py-2 bg-base-200">
	<div class="flex flex-wrap">
		<Breadcrumb />
		<ThemeController />
	</div>
	<h1 class="text-4xl font-semibold">Starting SEO as your Home</h1>
</header>
<main class="flex flex-wrap max-md:gap-5 p-2 md:p-5">
	<div class="{theaterStatus ? '' : 'contents'} w-full md:w-2/3">
		<div class="w-full max-md:sticky top-0 z-100">
			{#key videoIndex}
				<VideoPlayer {...videoData[videoIndex % 2]} />
			{/key}
		</div>
		<div class={theaterStatus || underMedium.current ? 'contents' : 'w-2/3'}>
			<div class="md:pr-5 max-md:contents flex flex-col gap-5">
				<Navigation />
				<CourseMaterial on:startQuizz={() => (isQuizzOpen = true)} />
				{#if !underMedium.current}
					<Comments />
				{/if}
			</div>
		</div>
	</div>
	<div class="w-full md:w-1/3 flex flex-col gap-5 px-2 pt-10 md:pt-2 md:pl-5" id="Curriculm">
		<h2 class="text-2xl font-semibold">Topics for This Course</h2>
		<Progress initialValue="63" />
		<Week weekTitle="Course Introduction" weekNum="1-4" weekContent={week1_4} />
		<Week weekTitle="JavaScript Language Basics" weekNum="5-8" weekContent={week5_8} />
		<Week weekTitle="Components & Databinding" weekNum="5-8" weekContent={week5_8} />
	</div>
	{#if underMedium.current}
		<div class="pr-5">
			<Comments />
		</div>
	{/if}
</main>
