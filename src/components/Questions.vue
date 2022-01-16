<template>
  <div>
    <div
      class="largeScreen xLargeScreen ml-10 mr-10 ml-md-16 mr-md-16"
      v-for="(question, i) in questions"
      :key="i"
    >
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

<style scoped>
@media screen and (min-width: 1264px) {
  .largeScreen {
    padding-left: 200px;
    padding-right: 200px;
  }
}
@media screen and (min-width: 1904px) {
  .xLargeScreen {
    padding-left: 400px;
    padding-right: 400px;
  }
}
</style>
