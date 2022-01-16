<template>
  <div class="text-h6 text-center mt-10 mb-5 grey--text text--darken-2">
    <div class="text-decoration-underline">Results:</div>
    <div>You Got {{ this.correctNum }} / 5 questions correct</div>
    <div class="red--text">{{ (100 * this.correctNum) / 5 }}%</div>
  </div>
</template>

<script>
export default {
  name: 'Result',
  props: {
    correctNum: Number,
  },
}
</script>
