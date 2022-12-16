<template>
  <div>
    <h1>Quiz App</h1>
    <p v-if="completed">You have completed the quiz!</p>
    <p v-else>Question {{ currentQuestionIndex + 1 }} of {{ questions.length }}</p>
    <p>{{ currentQuestion.question }}</p>
    <ul>
      <li v-for="(answer, index) in currentQuestion.answers" :key="index">
        <button @click="selectAnswer(answer)">{{ answer }}</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentQuestionIndex: 0,
      questions: [
        {
          question: 'What is the capital of France?',
          answers: ['Paris', 'London', 'Berlin', 'Madrid'],
          correctAnswer: 'Paris'
        },
        {
          question: 'What is the tallest mountain in the world?',
          answers: ['Mount Everest', 'K2', 'Kangchenjunga', 'Lhotse'],
          correctAnswer: 'Mount Everest'
        },
        {
          question: 'What is the largest ocean in the world?',
          answers: ['Atlantic Ocean', 'Pacific Ocean', 'Indian Ocean', 'Southern Ocean'],
          correctAnswer: 'Pacific Ocean'
        }
      ],
      completed: false
    }
  },
  computed: {
    currentQuestion() {
      return this.questions[this.currentQuestionIndex]
    }
  },
  methods: {
    selectAnswer(answer) {
      if (answer === this.currentQuestion.correctAnswer) {
        // advance to the next question
        this.currentQuestionIndex++
      }
      if (this.currentQuestionIndex === this.questions.length) {
        // quiz is completed
        this.completed = true
      }
    }
  }
}
</script>
