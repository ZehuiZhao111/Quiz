<template>
  <h1 class="header red darken-4">
    <p class="grey--text text--lighten-4 lift-text">Quiz Application</p>
  </h1>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style scoped>
/* extra small(specail case) */
@media screen and (max-width: 326px) {
  .header {
    font-size: 26px !important;
  }
  .lift-text {
    margin-top: -15px;
  }
}
@media screen and (max-width: 768px) {
  .header {
    height: 100px;
    padding-top: 27px;
    padding-left: 80px;
    font-size: 32px;
    font-weight: 400;
  }
}
@media screen and (min-width: 768px) {
  .header {
    height: 60px;
    padding-top: 12px;
    padding-left: 60px;
    font-size: 25px;
    font-weight: 400;
  }
}
@media screen and (min-width: 992px) {
  .header {
    height: 30px;
    padding-left: 10px;
    padding-top: 2px;
    font-size: 18px;
    font-weight: 400;
  }
}
</style>
