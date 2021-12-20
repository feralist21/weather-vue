<template>
  <div class="sort-form__group">
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--checkbox">
      <input
        id="rainy"
        name="weather-conditions"
        type="checkbox"
        value="rainy"
      />
      <label aria-label="Дождливо" for="rainy">
        <span class="icon icon--rainy"></span>
      </label>
    </div>
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--checkbox">
      <input
        id="sunny"
        name="weather-conditions"
        type="checkbox"
        value="sunny"
      />
      <label aria-label="Солнечно" for="sunny">
        <span class="icon icon--sunny"></span>
      </label>
    </div>
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--checkbox">
      <input
        id="cloudy"
        name="weather-conditions"
        type="checkbox"
        value="cloudy"
      />
      <label aria-label="Облачно" for="cloudy">
        <span class="icon icon--cloudy"></span>
      </label>
    </div>
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--checkbox">
      <input
        id="snowy"
        name="weather-conditions"
        type="checkbox"
        value="snowy"
      />
      <label aria-label="Снежно" for="snowy">
        <span class="icon icon--snowy"></span>
      </label>
    </div>
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--checkbox">
      <input
        id="stormy"
        name="weather-conditions"
        type="checkbox"
        value="stormy"
      />
      <label aria-label="Торнадо" for="stormy">
        <span class="icon icon--stormy"></span>
      </label>
    </div>
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--checkbox">
      <input
        id="blizzard"
        name="weather-conditions"
        type="checkbox"
        value="blizzard"
      />
      <label aria-label="Гроза" for="blizzard">
        <span class="icon icon--blizzard"></span>
      </label>
    </div>
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--checkbox">
      <input
        id="metorite"
        name="weather-conditions"
        type="checkbox"
        value="metorite"
      />
      <label aria-label="Метеоритный дождь" for="metorite">
        <span class="icon icon--metorite"></span>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: "filter-weather",
};
</script>

<style></style>
