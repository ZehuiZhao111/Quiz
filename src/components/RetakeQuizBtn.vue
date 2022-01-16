<template>
  <v-btn
    class="btn"
    elevation="2"
    width="200px"
    :style="{
      left: '50%',
      transform: 'translateX(-50%)',
    }"
    @click="reloadPage"
    >Retake the quiz</v-btn
  >
</template>

<script>
export default {
  name: 'RetakeQuizBtn',
  methods: {
    reloadPage() {
      window.location.reload()
    },
  },
}
</script>
