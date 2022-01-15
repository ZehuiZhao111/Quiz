<template>
  <div>
    <div>Results:</div>
    <div>You Got {{ this.correctNum }} / 5 questions correct</div>
    <div>{{ (100 * this.correctNum) / 5 }} %</div>
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
