<script>
  import { ChevronLeft, Clock } from "@lucide/svelte";
  
  let currentQuestion = $state(0);
  let selectedAnswers = $state({});
  let isTransitioning = $state(false);
  let slideDirection = $state('left');

  const questions = [
    {
      id: 1,
      question: "Among the following status of India, which one has the oldest rock formations in the country?",
      options: ["Assam", "Bihar", "Karnataka", "Uttar Pradesh"],
      correctAnswer: 1
    },
    {
      id: 2,
      question: "Which river is known as the 'Sorrow of Bihar'?",
      options: ["Ganges", "Kosi", "Yamuna", "Brahmaputra"],
      correctAnswer: 1
    },
    {
      id: 3,
      question: "What is the capital of Maharashtra?",
      options: ["Pune", "Nagpur", "Mumbai", "Nashik"],
      correctAnswer: 2
    },
    {
      id: 4,
      question: "Which is the largest state in India by area?",
      options: ["Madhya Pradesh", "Rajasthan", "Maharashtra", "Uttar Pradesh"],
      correctAnswer: 1
    },
    {
      id: 5,
      question: "The Tropic of Cancer passes through how many Indian states?",
      options: ["6", "7", "8", "9"],
      correctAnswer: 2
    }
  ];

  function handleAnswerSelect(questionIndex, answerIndex) {
    selectedAnswers = {
      ...selectedAnswers,
      [questionIndex]: answerIndex
    };

    // Auto-advance to next question after selection
    setTimeout(() => {
      if (questionIndex < questions.length - 1) {
        handleNextQuestion();
      }
    }, 300);
  }

  function handleNextQuestion() {
    if (currentQuestion < questions.length - 1) {
      isTransitioning = true;
      slideDirection = 'left';
      setTimeout(() => {
        currentQuestion = currentQuestion + 1;
        isTransitioning = false;
      }, 300);
    }
  }

  function handlePrevQuestion() {
    if (currentQuestion > 0) {
      isTransitioning = true;
      slideDirection = 'right';
      setTimeout(() => {
        currentQuestion = currentQuestion - 1;
        isTransitioning = false;
      }, 300);
    }
  }

  function handleQuestionDotClick(index) {
    if (index !== currentQuestion) {
      isTransitioning = true;
      slideDirection = index > currentQuestion ? 'left' : 'right';
      setTimeout(() => {
        currentQuestion = index;
        isTransitioning = false;
      }, 300);
    }
  }
</script>

<div class="min-h-screen bg-gradient-to-br from-blue-500 via-blue-600 to-indigo-700 flex items-center justify-center p-4">
  <div class="w-full max-w-md bg-indigo-600 rounded-3xl shadow-2xl overflow-hidden">
    <!-- Header -->
    <div class="p-6 pb-4">
      <div class="flex items-center justify-between mb-6">
        <button 
          onclick={handlePrevQuestion}
          disabled={currentQuestion === 0}
          class="btn-ghost bg-transparent text-white p-2 disabled:opacity-50"
        >
          <ChevronLeft size={28} />
        </button>
        
        <div class="bg-yellow-400 px-6 py-2 rounded-full flex items-center gap-2">
          <Clock size={20} class="text-gray-800" />
          <span class="font-bold text-gray-800">09:32</span>
        </div>
        
        <div class="w-10"></div>
      </div>

      <!-- Progress Dots -->
      <div class="flex justify-center gap-3">
        {#each questions as _, index}
          <button
            onclick={() => handleQuestionDotClick(index)}
            class="w-12 h-12 rounded-full flex items-center justify-center font-semibold transition-all duration-300 {
              index === currentQuestion
                ? 'bg-white text-indigo-600 scale-110'
                : index < currentQuestion || selectedAnswers[index] !== undefined
                ? 'bg-white/30 text-white border-2 border-white'
                : 'bg-transparent text-white border-2 border-white/50'
            }"
          >
            {index + 1}
          </button>
        {/each}
      </div>
    </div>

    <!-- Question Card with Slide Animation -->
    <div class="relative overflow-hidden">
      <div
        class="transition-transform duration-300 ease-in-out {
          isTransitioning
            ? slideDirection === 'left'
              ? '-translate-x-full'
              : 'translate-x-full'
            : 'translate-x-0'
        }"
      >
        <div class="bg-white rounded-t-3xl p-8 min-h-[500px]">
          <h2 class="text-xl font-bold text-gray-800 mb-8">
            {currentQuestion + 1}.
          </h2>
          
          <p class="text-xl text-gray-700 mb-8 leading-relaxed">
            {questions[currentQuestion].question}
          </p>

          <div class="space-y-4">
            {#each questions[currentQuestion].options as option, index}
              {@const isSelected = selectedAnswers[currentQuestion] === index}
              <button
                onclick={() => handleAnswerSelect(currentQuestion, index)}
                class="w-full flex items-center gap-4 p-5 rounded-2xl transition-all duration-200 {
                  isSelected
                    ? 'bg-indigo-600 text-white shadow-lg scale-105'
                    : 'bg-gray-50 text-gray-700 hover:bg-gray-100'
                }"
              >
                <div
                  class="w-6 h-6 rounded border-2 flex items-center justify-center {
                    isSelected
                      ? 'border-white bg-white'
                      : 'border-gray-300'
                  }"
                >
                  {#if isSelected}
                    <div class="w-3 h-3 bg-indigo-600 rounded"></div>
                  {/if}
                </div>
                <span class="text-lg font-medium">{option}</span>
              </button>
            {/each}
          </div>

          <!-- Navigation hint -->
          {#if currentQuestion === questions.length - 1 && selectedAnswers[currentQuestion] !== undefined}
            <div class="mt-8 text-center">
              <button class="btn btn-success text-white px-8 py-3 rounded-full font-semibold">
                Submit Quiz
              </button>
            </div>
          {/if}
        </div>
      </div>
    </div>
  </div>
</div>