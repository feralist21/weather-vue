<template>
  <div class="sort-form__group">
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--search">
      <input
        id="search"
        type="search"
        name="city-search"
        placeholder="Название города"
        v-model="city"
        v-on:input="findCity"
      />
      <label for="search" aria-label="Поиск городов"></label>
    </div>
  </div>
</template>

<script>
export default {
  name: "filter-city",
  data() {
    return {
      city: "",
    };
  },
  methods: {
    findCity() {
      this.$emit("filtered", this.city);
    },
  },
};
</script>

<style></style>
