<script>
	import QuestionContent from './QuestionContent.svelte';
	import QuestionNums from './QuestionNums.svelte';
	import Timer from './Timer.svelte';

	let currentQuestion = $state(1);
	const questions = [
		{
			id: 1,
			question:
				'Among the following status of India, which one has the oldest rock formations in the country?',
			options: ['Assam', 'Bihar', 'Karnataka', 'Uttar Pradesh'],
			correctAnswer: 1
		},
		{
			id: 2,
			question: "Which river is known as the 'Sorrow of Bihar'?",
			options: ['Ganges', 'Kosi', 'Yamuna', 'Brahmaputra'],
			correctAnswer: 1
		},
		{
			id: 3,
			question: 'What is the capital of Maharashtra?',
			options: ['Pune', 'Nagpur', 'Mumbai', 'Nashik'],
			correctAnswer: 2
		},
		{
			id: 4,
			question: 'Which is the largest state in India by area?',
			options: ['Madhya Pradesh', 'Rajasthan', 'Maharashtra', 'Uttar Pradesh'],
			correctAnswer: 1
		},
		{
			id: 5,
			question: 'The Tropic of Cancer passes through how many Indian states?',
			options: ['6', '7', '8', '9'],
			correctAnswer: 2
		}
	];
</script>

<input type="checkbox" id="my_modal_4" class="modal-toggle" />
<div class="modal" role="dialog">
	<main
		class="modal-box flex flex-col overflow-x-hidden items-center justify-center gap-8 max-w-none w-full h-full rounded-none bg-[#3f55b7]"
	>
		<label for="my_modal_4" class="btn btn-circle w-6 h-6 absolute top-3 right-3">X</label>
		<Timer />
		<QuestionNums
			{questions}
			currentQuestion={{
				get currentQuestion() {
					return currentQuestion;
				},
				set currentQuestion(val) {
					currentQuestion = val;
				}
			}}
		/>
		<div class="center w-fit">
			<div
				class="flex w-90 px-4 overflow-x-hidden self-start slider"
				style={`--current-slide-index: ${currentQuestion};`}
			>
				{#each questions as question}
					<QuestionContent question={{ ...question, currentQuestion }} />
				{/each}
			</div>
		</div>
	</main>
</div>
