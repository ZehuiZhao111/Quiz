<template>
  <v-card
    elevation="5"
    class="mx-auto my-12"
    max-width="600px"
    :class="{
      correct: isSubmit && arrEqual(answer, question.answer),
      wrong: isSubmit && !arrEqual(answer, question.answer),
      unAnswered: !isSubmit && answer.length === 0 && submitIsClicked,
    }"
  >
    <v-card-title>{{ question.des }} </v-card-title>
    <v-divider class="mx-4"></v-divider>
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
        }"
      ></v-checkbox>
    </div>
    <div v-show="isSubmit">
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
