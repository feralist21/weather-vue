<template>
  <div class="small-card">
    <span class="small-card__city"> {{ smallCity.city }} </span>
    <span v-if="smallCity.temperature > 0" class="small-card__temperature"
      >+{{ smallCity.temperature }}</span
    >
    <span
      v-else-if="smallCity.temperature === 0"
      class="small-card__temperature"
      >{{ smallCity.temperature }}</span
    >
    <span v-else class="small-card__temperature">{{
      smallCity.temperature
    }}</span>
    <span class="icon icon--strips-small"></span>
  </div>
</template>

<script>
export default {
  name: "small-card",
  props: {
    smallCity: Object,
  },
};
</script>

<style></style>
