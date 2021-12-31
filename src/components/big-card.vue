<template>
  <div class="big-card">
    <div class="big-card__header">
      <span class="icon icon--strips-big"></span>
      <span class="big-card__city"> {{ fullInfo.city }} </span>
    </div>
    <div class="big-card__content">
      <div class="big-card__content-wrapper">
        <div class="big-card__weather-conditions">
          <span
            v-if="fullInfo.weather.rainy === true"
            class="icon icon--rainy"
          ></span>
          <span
            v-if="fullInfo.weather.sunny === true"
            class="icon icon--sunny"
          ></span>
          <span
            v-if="fullInfo.weather.cloudy === true"
            class="icon icon--cloudy"
          ></span>
          <span
            v-if="fullInfo.weather.snowy === true"
            class="icon icon--snowy"
          ></span>
          <span
            v-if="fullInfo.weather.stormy === true"
            class="icon icon--stormy"
          ></span>
          <span
            v-if="fullInfo.weather.blizzard === true"
            class="icon icon--blizzard"
          ></span>
          <span
            v-if="fullInfo.weather.metorite === true"
            class="icon icon--metorite"
          ></span>
          <!-- <span class="icon icon--meteor-shower"></span> -->
          <!-- <span class="icon icon--tornado"></span> -->
        </div>
        <div class="big-card__wind">
          <span class="icon icon--wind"></span>
          <span class="big-card__wind-info"
            >Ветер {{ fullInfo.wind.direction }},
            {{ fullInfo.wind.speed }} м/с</span
          >
        </div>
      </div>
      <!-- <span v-if="fullInfo.temperature < 0" class="big-card__temperature">
        +{{ fullInfo.temperature }}°</span
      >
      <span v-else-if="city.temperature === 0" class="big-card__temperature">
        {{ fullInfo.temperature }}°</span
      >
      <span v-else class="big-card__temperature"
        >{{ fullInfo.temperature }}°</span
      > -->
      <span v-if="fullInfo.temperature > 0" class="big-card__temperature">
        +{{ fullInfo.temperature }}°</span
      >
      <span v-else class="big-card__temperature">
        {{ fullInfo.temperature }}°</span
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "big-card",
  props: {
    fullInfo: Object,
  },
};
</script>

<style></style>
