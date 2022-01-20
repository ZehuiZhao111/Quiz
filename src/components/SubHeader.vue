<template>
  <h2 class="subHeader">
    <div class="grey--text text--darken-2">
      Quiz 1 - HTML / CSS / JS Practice
    </div>
  </h2>
</template>

<script>
export default {
  name: 'SubHeader',
}
</script>

<style scoped>
@media screen and (max-width: 768px) {
  .subHeader {
    margin-left: 40px;
    margin-top: 45px;
    font-size: 40px;
    font-weight: 400;
  }
}
@media screen and (min-width: 768px) {
  .subHeader {
    margin-left: 70px;
    margin-top: 20px;
    font-size: 27px;
    font-weight: 400;
  }
}
@media screen and (min-width: 992px) {
  .subHeader {
    margin-left: 250px;
    margin-top: 20px;
    font-size: 35px;
    font-weight: 400;
  }
}
</style>
