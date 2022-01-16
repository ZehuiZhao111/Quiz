<template>
  <v-card
    elevation="5"
    class="my-12 rounded-lg"
    :class="{
      correct: isSubmit && arrEqual(answer, question.answer),
      wrong: isSubmit && !arrEqual(answer, question.answer),
      unAnswered: !isSubmit && answer.length === 0 && submitIsClicked,
    }"
  >
    <v-card-title class="grey--text text--darken-2"
      >{{ question.id + 1 }}. {{ question.des }}
    </v-card-title>
    <v-divider></v-divider>
    <div v-for="(option, i) in question.options" :key="i">
      <v-checkbox
        @change="onChange(question.id)"
        v-model="answer"
        :label="option"
        :value="option"
        :class="{
          highlight:
            isSubmit &&
            !arrEqual(answer, question.answer) &&
            question.answer.includes(option),
          whiteText:
            isSubmit &&
            !arrEqual(answer, question.answer) &&
            question.answer.includes(option),
        }"
        class="adjust-content ml-4 mr-4 mb-n3 grey--text rounded-lg"
      ></v-checkbox>
    </div>
    <div
      class="text-right mt-5 mr-5 mb-2 font-weight-medium"
      :class="{
        correctAns: arrEqual(answer, question.answer),
        wrongAns: !arrEqual(answer, question.answer),
      }"
      v-show="isSubmit"
    >
      {{ arrEqual(answer, question.answer) ? 'Correct' : 'Wrong' }}
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
      answer: [],
    }
  },
  methods: {
    onChange(id) {
      this.$emit('add-answer', {
        id: id,
        answer: this.answer,
      })
    },
    arrEqual(arr1, arr2) {
      const arr1Copy = [...arr1]
      const arr2Copy = [...arr2]
      arr1Copy.sort()
      arr2Copy.sort()
      if (JSON.stringify(arr1Copy) !== JSON.stringify(arr2Copy)) {
        return false
      }
      return true
    },
  },
}
</script>

<style scoped>
.highlight {
  background: #32cd32;
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
</style>
