<template>
  <div class="text-xs-center">
    <v-btn
      elevation="2"
      width="200px"
      :style="{
        left: '50%',
        transform: 'translateX(-50%)',
      }"
      @click="onClick"
      >Submit</v-btn
    >
    <div v-show="showAlert">
      <v-alert color="red lighten-2" dark>
        Answer all questions before submitting. Unanswered questions are
        displayed in yellow
      </v-alert>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Button',
  props: {
    answers: Array,
    isSubmit: Boolean,
  },
  data() {
    return {
      showAlert: false,
    }
  },
  methods: {
    onClick() {
      for (let i = 0; i < this.answers.length; i++) {
        const answer = this.answers[i]
        if (answer === undefined || answer.length === 0) {
          this.showAlert = true
          this.isSubmit = false
          this.$emit('show-result', this.isSubmit)
          return
        }
      }
      this.showAlert = false
      this.isSubmit = true
      this.$emit('show-result', this.isSubmit)
    },
  },
}
</script>
