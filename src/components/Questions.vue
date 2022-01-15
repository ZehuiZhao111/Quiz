<template>
  <div>
    <div v-for="(question, i) in questions" :key="i">
      <Question
        @add-answer="addAnswer"
        :question="question"
        :isSubmit="isSubmit"
        :submitIsClicked="submitIsClicked"
      />
    </div>
  </div>
</template>

<script>
import Question from './Question.vue'
export default {
  name: 'Questions',
  components: {
    Question,
  },
  props: {
    questions: Array,
    isSubmit: Boolean,
    submitIsClicked: Boolean,
  },
  methods: {
    addAnswer(obj) {
      this.$emit('add-answer', obj)
    },
  },
}
</script>
