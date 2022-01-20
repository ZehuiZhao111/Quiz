<template>
  <v-card
    elevation="5"
    class="my-10 rounded-lg"
    :class="{
      correct: isSubmit && answer == question.answer,
      wrong: isSubmit && answer !== question.answer,
      unAnswered: !isSubmit && answer.length === 0 && submitIsClicked,
    }"
  >
    <v-card-title class="grey--text text--darken-2 card-title"
      >{{ question.id + 1 }}. {{ question.des }}
    </v-card-title>
    <v-radio-group
      class="remove-gap"
      v-model="answer"
      @change="onChange(question.id)"
    >
      <div v-for="(option, i) in question.options" :key="i">
        <v-radio
          :class="{
            highlight:
              isSubmit &&
              answer !== question.answer &&
              question.answer.includes(option),
            whiteText:
              isSubmit &&
              answer !== question.answer &&
              question.answer.includes(option),
          }"
          class="adjust-content ml-4 mb-4 mr-4 grey--text rounded-lg"
          :label="option"
          :value="option"
        ></v-radio>
      </div>
    </v-radio-group>
    <div
      class="text-right mt-n2 mr-5 mb-2 font-weight-medium"
      :class="{
        correctAns: answer == question.answer,
        wrongAns: answer !== question.answer,
      }"
      v-show="isSubmit"
    >
      {{ answer == question.answer ? 'Correct' : 'Wrong' }}
    </div>
  </v-card>
</template>
<script>
export default {
  name: 'Question',
  props: {
    question: Object,
    isSubmit: Boolean,
    submitIsClicked: Boolean,
  },
  data() {
    return {
      answer: '',
    }
  },
  methods: {
    onChange(id) {
      this.$emit('add-answer', {
        id: id,
        answer: this.answer,
      })
    },
  },
}
</script>

<style scoped>
.highlight {
  background: #32cd32;
  border: 1px solid green;
}
.unAnswered {
  border: 2px solid yellow !important;
}
.correct {
  border: 2px solid #32cd32 !important;
}
.wrong {
  border: 2px solid #b71c1c !important;
}

.whiteText /deep/ label {
  color: white !important;
}

.grey--text /deep/ label {
  color: #7b7575;
  font-weight: 450;
}
.adjust-content {
  max-width: 800px;
  min-height: 40px;
  overflow: hidden;
}

::v-deep .v-input__slot {
  margin-bottom: 0px !important;
  margin-top: 10px !important;
}
.correctAns {
  color: #32cd32;
}
.wrongAns {
  color: #b71c1c;
}
.remove-gap {
  margin-top: -5px;
}
@media screen and (max-width: 768px) {
  .card-title {
    font-size: 24px;
  }
  .grey--text /deep/ label {
    font-size: 19px;
  }
}
@media screen and (min-width: 768px) {
  .card-title {
    font-size: 20px;
  }
  .grey--text /deep/ label {
    font-size: 17px;
  }
}
@media screen and (min-width: 992px) {
  .card-title {
    font-size: 18px;
  }
  .grey--text /deep/ label {
    font-size: 16px;
  }
}
</style>
