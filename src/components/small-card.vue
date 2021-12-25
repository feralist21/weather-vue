<template>
  <div class="small-card">
    <span class="small-card__city"> {{ city.city }} </span>
    <span v-if="city.temperature > 0" class="small-card__temperature"
      >+{{ city.temperature }}</span
    >
    <span v-else-if="city.temperature === 0" class="small-card__temperature">{{
      city.temperature
    }}</span>
    <span v-else class="small-card__temperature">{{ city.temperature }}</span>
    <span class="icon icon--strips-small"></span>
  </div>
</template>

<script>
export default {
  name: "small-card",
  props: {
    city: Object,
  },
};
</script>

<style></style>
