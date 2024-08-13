<template lang="pug">
.victorina
  h1 Victorina
  transition(name="fade" mode="out-in")
    .question(v-if="currentQuestion" :key="currentQuestion.id")
      h2 {{ currentQuestion.question }}
      ul
        li(
          v-for="answer in currentQuestion.answers"
          :key="answer.id"
          @click="selectAnswer(currentQuestion.id, answer.id)"
          :class="{\
            selected: currentQuestion.selectedAnswer === answer.id,\
            correct: showResult && answer.correct,\
            incorrect: showResult && currentQuestion.selectedAnswer === answer.id && !answer.correct\
          }"
        )
          | {{ answer.text }}
          span.checkmark(v-if="currentQuestion.selectedAnswer === answer.id") ✓
  .navigation
    button(@click="previousQuestion" :disabled="currentQuestionIndex === 0") Previous
    button(@click="nextQuestion" v-if="!isLastQuestion") Next
    button(@click="checkAnswers" v-if="isLastQuestion && allQuestionsAnswered") Finish Quiz
  p.result(v-if="showResult") Correct answers: {{ correctAnswers }} out of {{ questions.length }}
</template>

<script>
export default {
  data() {
    return {
      currentQuestionIndex: 0,
      questions: [
        {
          id: 1,
          question: 'What is the capital of France?',
          answers: [
            { id: 1, text: 'London', correct: false },
            { id: 2, text: 'Berlin', correct: false },
            { id: 3, text: 'Paris', correct: true },
            { id: 4, text: 'Madrid', correct: false }
          ],
          selectedAnswer: null
        },
        {
          id: 2,
          question: 'Which planet is known as the Red Planet?',
          answers: [
            { id: 1, text: 'Venus', correct: false },
            { id: 2, text: 'Mars', correct: true },
            { id: 3, text: 'Jupiter', correct: false },
            { id: 4, text: 'Saturn', correct: false }
          ],
          selectedAnswer: null
        },
        {
          id: 3,
          question: 'Who painted the Mona Lisa?',
          answers: [
            { id: 1, text: 'Vincent van Gogh', correct: false },
            { id: 2, text: 'Pablo Picasso', correct: false },
            { id: 3, text: 'Leonardo da Vinci', correct: true },
            { id: 4, text: 'Michelangelo', correct: false }
          ],
          selectedAnswer: null
        },
        {
          id: 4,
          question: 'What is the largest ocean on Earth?',
          answers: [
            { id: 1, text: 'Atlantic Ocean', correct: false },
            { id: 2, text: 'Indian Ocean', correct: false },
            { id: 3, text: 'Arctic Ocean', correct: false },
            { id: 4, text: 'Pacific Ocean', correct: true }
          ],
          selectedAnswer: null
        }
      ],
      correctAnswers: 0,
      showResult: false
    }
  },
  computed: {
    currentQuestion() {
      return this.questions[this.currentQuestionIndex]
    },
    isLastQuestion() {
      return this.currentQuestionIndex === this.questions.length - 1
    },
    allQuestionsAnswered() {
      return this.questions.every(q => q.selectedAnswer !== null)
    }
  },
  methods: {
    selectAnswer(questionId, answerId) {
      const question = this.questions.find(q => q.id === questionId)
      if (question) {
        question.selectedAnswer = answerId
      }
    },
    checkAnswers() {
      this.correctAnswers = this.questions.filter(q => 
        q.answers.find(a => a.id === q.selectedAnswer && a.correct)
      ).length
      this.showResult = true
    }
  }
}
</script>

<style scoped lang="scss">
.victorina {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;

  h1 {
    color: #333;
    text-align: center;
    margin-bottom: 30px;
  }

  .question {
    background-color: #f5f5f5;
    border-radius: 8px;
    padding: 15px;
    margin-bottom: 20px;

    h2 {
      color: #444;
      font-size: 1.2em;
      margin-bottom: 10px;
    }

    ul {
      list-style-type: none;
      padding: 0;
    }

    li {
      background-color: #fff;
      border: 1px solid #ddd;
      border-radius: 4px;
      padding: 10px;
      margin-bottom: 8px;
      cursor: pointer;
      transition: background-color 0.3s;

      &:hover {
        background-color: #e6e6e6;
      }

      &.correct {
        background-color: #d4edda;
        border-color: #c3e6cb;
      }

      &.incorrect {
        background-color: #f8d7da;
        border-color: #f5c6cb;
      }

      .checkmark {
        margin-left: 10px;
      }
    }
  }

  button {
    display: block;
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    font-size: 1em;
    cursor: pointer;
    transition: background-color 0.3s;

    &:hover {
      background-color: #0056b3;
    }
  }

  .result {
    text-align: center;
    font-size: 1.2em;
    margin-top: 20px;
    font-weight: bold;
  }
}
</style>