<template>
  <div class="big-card">
    <div class="big-card__header">
      <span class="icon icon--strips-big"></span>
      <span class="big-card__city">Великий Новгород</span>
    </div>
    <div class="big-card__content">
      <div class="big-card__content-wrapper">
        <div class="big-card__weather-conditions">
          <span class="icon icon--rainy"></span>
          <span class="icon icon--meteor-shower"></span>
          <span class="icon icon--tornado"></span>
        </div>
        <div class="big-card__wind">
          <span class="icon icon--wind"></span>
          <span class="big-card__wind-info">Ветер ЮВ, 0-1 м/с</span>
        </div>
      </div>
      <span class="big-card__temperature">+12°</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "big-card",
};
</script>

<style></style>
