<template>
  <v-app>
    <Header />
    <SubHeader />
    <div v-show="isSubmit">
      <Result :correctNum="correctNum" />
    </div>
    <Questions
      @add-answer="addAnswer"
      :questions="questions"
      :isSubmit="isSubmit"
      :submitIsClicked="submitIsClicked"
    />
    <Button @show-result="showResult" :answers="answers" :isSubmit="isSubmit" />
  </v-app>
</template>

<script>
import dummyQuestionData from './data/questions.json'
import Header from './components/Header.vue'
import SubHeader from './components/SubHeader.vue'
import Result from './components/Result.vue'
import Questions from './components/Questions.vue'
import Button from './components/Button.vue'

export default {
  name: 'App',

  components: {
    Header,
    SubHeader,
    Result,
    Questions,
    Button,
  },

  data() {
    return {
      questions: [],
      answers: new Array(5),
      isSubmit: false,
      correctNum: 0,
      submitIsClicked: false,
    }
  },
  methods: {
    addAnswer({ id, answer }) {
      this.answers = [
        ...this.answers.slice(0, id),
        answer,
        ...this.answers.slice(id + 1),
      ]
    },
    showResult(isSubmit) {
      this.submitIsClicked = true
      this.isSubmit = isSubmit
      if (this.isSubmit) {
        let count = 0
        for (let i = 0; i < this.answers.length; i++) {
          const answer = this.answers[i]
          const correctAns = this.questions[i].answer

          if (answer == correctAns) {
            count = count + 1
          }
        }
        this.correctNum = count
      }
    },
  },

  created() {
    this.questions = dummyQuestionData
  },
}
</script>
