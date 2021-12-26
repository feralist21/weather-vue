<template>
  <form action="#" method="GET">
    <sortBtn v-bind:cities="cit"></sortBtn>
    <filterCity></filterCity>
    <filterweather></filterweather>
  </form>
</template>

<script>
import sortBtn from "./sort-btn";
import filterCity from "./filter-city";
import filterweather from "./filter-weather";

export default {
  name: "sort-form",
  components: {
    sortBtn,
    filterCity,
    filterweather,
  },
  props: {
    cit: [Array, String],
  },
};
</script>

<style></style>
