<script>
	import { getContext, onMount } from 'svelte';
	import videojs from 'video.js';
	import 'video.js/dist/video-js.css';
	import LandscapeFullscreen from 'videojs-landscape-fullscreen';
	import TheaterMode from './TheaterMode.svelte';

	videojs.registerPlugin('landscapeFullscreen', LandscapeFullscreen);

	let { vidPath, thumbPath } = $props();
	let playing = $state(false);
	let videoElement = $state(null);
	let videoIndex = getContext('videoIndex');

	onMount(() => {
		const player = videojs(videoElement, {
			controls: true,
			fluid: true,
			playbackRates: [0.5, 0.75, 1, 1.25, 1.5, 2]
		});
		videoElement.addEventListener('ended', () => {
			videoIndex.data++;
		});

		return () => {
			if (player) {
				player.dispose();
			}
		};
	});
</script>

<div class="sticky w-full md:relative z-50 top-0">
	{#if playing}
		<TheaterMode />
	{/if}
	<!-- svelte-ignore a11y_media_has_caption -->
	<video
		src={vidPath}
		poster={thumbPath}
		bind:this={videoElement}
		class="video-js"
		style:border-radius="var(--radius-lg)"
	></video>
	<button
		title="Play"
		id="Play"
		class="w-full h-full top-0 absolute center rounded bg-black/40"
		style:display={playing ? 'none' : null}
		onclick={() => {
			playing = true;
			videoElement.play();
		}}
	>
		<div class="btn btn-circle hover:bg-[#1ab69d] hover:[&>*]:border-white w-20 h-20">
			<div
				id="play-pause-btn"
				class="w-1 h-0 border-red-600 rounded-sm translate-x-[20%] border-b-[10px] border-t-[10px] border-l-[15px] !border-b-transparent !border-t-transparent"
			></div>
		</div>
	</button>
</div>

<style>
	:global(.video-js .vjs-big-play-button) {
		display: none !important;
	}
</style>
