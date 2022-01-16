<template>
  <div class="text-center">
    <v-btn elevation="2" width="200px" @click="reloadPage"
      >Retake the quiz</v-btn
    >
  </div>
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
