<script>
	import QuestionContent from './QuestionContent.svelte';
	import QuestionNums from './QuestionNums.svelte';
	import Timer from './Timer.svelte';
	import { getContext } from 'svelte';

	let quizzTime = getContext('quizzTime');
	let modal = $state(null);
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
	let userAnswers = $state(Array(questions.length).fill(null));
	let score = $state(0);
	let toastMessage = $state('');
	let toastClass = $state('');

	function handleAnswer(questionIndex, optionIndex) {
		userAnswers[questionIndex] = optionIndex;
		if (currentQuestion < questions.length) {
			currentQuestion++;
		}
	}

	function submitQuiz() {
		score = 0;
		for (let i = 0; i < questions.length; i++) {
			if (userAnswers[i] === questions[i].correctAnswer) {
				score++;
			}
		}
		toastMessage = `You got ${score} out of ${questions.length} questions right!`;
		if (score > questions.length / 2) {
			toastClass = 'alert-success';
		} else {
			toastClass = 'alert-error';
		}
		const toast = document.getElementById('toast');
		toast.classList.remove('hidden');
		setTimeout(() => {
			toast.classList.add('hidden');
		}, 5000);
		modal.checked = false;
		userAnswers = Array(questions.length).fill(null);
		currentQuestion = 1;
		quizzTime.time = -1;
	}
</script>

<input type="checkbox" id="my_modal_4" class="modal-toggle" bind:this={modal} title="Quizz" />
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
				{#each questions as question, i}
					<QuestionContent
						{question}
						selectedAnswer={userAnswers[i]}
						on:answer={(e) => handleAnswer(i, e.detail.optionIndex)}
					/>
				{/each}
			</div>
		</div>
		{#if currentQuestion === questions.length}
			<button
				class="btn btn-primary bg-[#1ab69d] text-white disabled:opacity-50"
				onclick={submitQuiz}
				disabled={userAnswers.some((answer) => answer === null)}
			>
				Submit
			</button>
		{/if}
	</main>
</div>
<div id="toast" class="toast toast-top toast-right hidden z-[100]">
	<div class={`alert ${toastClass}`}>
		<span class="text-white font-semibold">{toastMessage}</span>
	</div>
</div>
