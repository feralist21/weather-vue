<template>
  <div class="sort-form__group">
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--radio">
      <input
        id="alphabet-sort"
        type="radio"
        name="alphabet-sort"
        value="alphabet-sort"
        v-on:click="sortAlphabet"
      />
      <label for="alphabet-sort" aria-label="Сортировка по алфавиту">
        <span class="icon icon--arrow-down"></span>
      </label>
    </div>
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--radio">
      <input
        id="alphabet-sort-reverse"
        type="radio"
        name="alphabet-sort"
        value="alphabet-sort-reverse"
        v-on:click="sortAlphabetReverse"
      />
      <label
        for="alphabet-sort-reverse"
        aria-label="Сортировка по алфавиту в обратном направлении"
      >
        <span class="icon icon--arrow-up"></span>
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: "sort-btn",
  props: {
    cities: [String, Array],
  },
  methods: {
    sortAlphabet() {
      return this.cities.sort((a, b) => (a.city > b.city ? 1 : -1));
    },
    sortAlphabetReverse() {
      return this.cities.sort((a, b) => (a.city < b.city ? 1 : -1));
    },
  },
};
</script>

<style></style>
