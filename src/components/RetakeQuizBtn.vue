<template>
  <button @click="reloadPage">Retake the quiz</button>
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
