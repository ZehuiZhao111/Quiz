<template>
  <h1
    class="mobileWidth text-h6 text-md-h5 text-lg-h4 text-xl-h4 red darken-4 pl-10"
  >
    <p class="grey--text text--lighten-4 mb-0">Quiz Application</p>
  </h1>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style scoped>
@media screen and (max-width: 600px) {
  .mobileWidth {
    height: 60px;
    padding-top: 13px;
  }
}
@media screen and (max-width: 205px) {
  .mobileWidth {
    height: 70px;
    padding-top: 2px;
  }
}
</style>
