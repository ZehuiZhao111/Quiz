<template>
  <div class="text-xs-center mb-16">
    <v-btn
      elevation="2"
      width="100px"
      :style="{
        left: '50%',
        transform: 'translateX(-50%)',
      }"
      class="btn"
      @click="onClick"
      >Submit</v-btn
    >
    <div class="alert">
      <v-alert v-show="showAlert" dark class="mt-5 text-center alertMsg">
        Answer all questions before submitting. Unanswered questions are
        displayed in yellow.
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

<style scoped>
.alert {
  display: flex;
  justify-content: center;
  align-items: center;
}
.alertMsg {
  color: red;
  background-color: transparent;
}
.btn {
  background-color: green !important;
  border: 1px solid black;
  color: white !important;
  text-transform: none;
}
</style>
