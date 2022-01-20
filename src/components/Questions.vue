<template>
  <div class="gap-top">
    <div class="questions" v-for="(question, i) in questions" :key="i">
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
@media screen and (max-width: 768px) {
  .questions {
    margin-left: 45px;
    margin-right: 45px;
  }
}
@media screen and (min-width: 768px) {
  .questions {
    margin-left: 30px;
    margin-right: 30px;
  }
  .gap-top {
    margin-top: -20px;
  }
}
@media screen and (min-width: 992px) {
  .questions {
    margin-left: 250px;
    margin-right: 250px;
  }
}
</style>
