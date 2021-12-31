<template>
  <main id="app">
    <section class="weather-app">
      <h1 class="visually-hidden">Прогноз погоды</h1>
      <div class="weather-app__content weather-content">
        <section class="sort-form weather-content__sort">
          <h2 class="visually-hidden">Форма сортировки</h2>
          <form action="#" method="GET">
            <sortBtn v-bind:cities="cities"></sortBtn>
            <filterCity v-on:filtered="getFilter"></filterCity>
            <filterweather></filterweather>
          </form>
        </section>
        <section class="weather-content__result">
          <h2 class="visually-hidden">Результаты сортировки</h2>
          <div class="weather-content__small-cards">
            <!-- <div class="small-card small-card--shadow">
              <span class="small-card__city"> Чебоксары </span>
              <span class="small-card__temperature">+17°</span>
              <span class="icon icon--strips-small"></span>
            </div>
            <div class="small-card small-card--empty"></div> -->
            <draggable v-bind:list="cities" group="cityList">
              <smallCard
                v-bind:smallCity="item"
                v-for="(item, idx) in filteredCities"
                v-bind:key="idx"
              ></smallCard>
            </draggable>
          </div>
          <div class="weather-content__big-cards">
            <div class="weather-content__help">
              Перетащите сюда города, погода в которых вам интересна
            </div>
            <div class="weather-content__big-inner">
              <draggable
                class="weather-content__draggable"
                v-bind:list="favoriteCities"
                group="cityList"
              >
                <bigCard
                  v-bind:fullInfo="item"
                  v-for="(item, ix) in favoriteCities"
                  v-bind:key="ix"
                >
                </bigCard>
              </draggable>
            </div>
          </div>
        </section>
      </div>
      <mainMap></mainMap>
    </section>
  </main>
</template>

<script>
import smallCard from "./components/small-card";
import bigCard from "./components/big-card";
import mainMap from "./components/main-map";
import sortBtn from "./components/sort-btn";
import filterCity from "./components/filter-city";
import filterweather from "./components/filter-weather";
import draggable from "vuedraggable";

export default {
  name: "App",
  components: {
    smallCard,
    bigCard,
    mainMap,
    sortBtn,
    filterCity,
    filterweather,
    draggable,
  },
  data() {
    return {
      cities: [],
      filter: "",
      favoriteCities: [],
    };
  },
  mounted() {
    let ths = this;
    fetch("https://geo-weather-json.herokuapp.com/db/")
      .then((responce) => responce.json())
      .then(function (data) {
        let sortCities = data.cities.sort((a, b) => (a.city > b.city ? 1 : -1));
        return (ths.cities = sortCities);
      });
  },
  methods: {
    getFilter(item) {
      this.filter = item;
    },
  },
  computed: {
    filteredCities: function () {
      let ths = this;
      return this.cities.filter(function (el) {
        return el.city.toLowerCase().indexOf(ths.filter.toLowerCase()) !== -1;
      });
    },
  },
};
</script>

<style src="./assets/css/style.css"></style>
