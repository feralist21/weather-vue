<template>
  <div class="sort-form__group">
    <div class="sort-form__input-wrapper input-wrapper input-wrapper--radio">
      <input
        id="alphabet-sort"
        type="radio"
        name="alphabet-sort"
        value="alphabet-sort"
        checked
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
};
</script>

<style></style>
