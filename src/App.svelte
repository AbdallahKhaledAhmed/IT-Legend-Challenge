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
	import ModalButton from './components/ModalButton.svelte';
	import { setContext } from 'svelte';
	import { MediaQuery } from 'svelte/reactivity';
	const underMedium = new MediaQuery('max-width: 768px');

	let videoData = $state({ vidPath: 'vid1(720).mp4', thumbPath: 'thumbnail.webp' });
	let quizzTime = $state(-1);
	let theaterMode = $state(false);
	let theaterStatus = $derived.by(() => (underMedium.current ? false : theaterMode));
	setContext('theaterStatus', {
		get status() {
			return theaterStatus;
		},
		set status(val) {
			theaterStatus = val;
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
	setContext('videoData', {
		get data() {
			return videoData;
		},
		set data(val) {
			videoData = val;
		}
	});
</script>

<PdfViewer path="CSharp.pdf" />
<Ask />
<Quizz />
<Leaderboard />

<header class="px-5 py-2 bg-[#f5f9fa]">
	<Breadcrumb />
	<h1 class="text-4xl font-semibold">Starting SEO as your Home</h1>
</header>
<main class="flex flex-wrap p-2 md:p-5">
	<div class={theaterStatus ? 'contents' : 'w-full md:w-2/3'}>
		<div class="w-full">
			{#key videoData}
				<VideoPlayer {...videoData} />
			{/key}
		</div>

		<div class="{theaterStatus ? 'w-full md:w-2/3':'w-full' } flex flex-col gap-5 md:pr-5 p-0">
			<ModalButton modalId="my_modal_1" btnClass="bg-gray-600"></ModalButton>
			<Navigation />
			<CourseMaterial />
			{#if !underMedium.current}
				<Comments />
			{/if}
		</div>
	</div>
	<div class="w-full md:w-1/3 flex flex-col gap-10 pl-5 pt-10 md:pt-2">
		<h2 class="text-2xl font-semibold">Topics for This Course</h2>
		<Progress initialValue="63" />
		<div id="Curriculm">
			<Week weekTitle="Course Introduction" weekNum="1-4" weekContent={week1_4} />
			<Week weekTitle="JavaScript Language Basics" weekNum="5-8" weekContent={week5_8} />
			<Week weekTitle="Components & Databinding" weekNum="5-8" weekContent={week5_8} />
		</div>
	</div>
	{#if underMedium.current}
		<Comments />
	{/if}
</main>
