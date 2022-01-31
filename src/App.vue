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
            <filterweather v-on:check-weather="getDataWeather"></filterweather>
          </form>
        </section>
        <section class="weather-content__result">
          <h2 class="visually-hidden">Результаты сортировки</h2>
          <div class="weather-content__small-cards">
            <draggable v-bind:list="cities" :sort="false" group="cityList">
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
                ghost-class="big-card--empty"
                v-bind:list="favoriteCities"
                group="cityList"
              >
                <bigCard
                  v-bind:fullInfo="item"
                  v-for="(item, ix) in filteredFavoriteCities"
                  v-bind:key="ix"
                >
                </bigCard>
              </draggable>
            </div>
          </div>
        </section>
      </div>
      <mainMap v-bind:favorCity="favoriteCities"></mainMap>
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
      weather: {},
    };
  },
  mounted() {
    fetch("https://geo-weather-json.herokuapp.com/db/")
      .then((responce) => responce.json())
      .then((data) => {
        let sortCities = data.cities.sort((a, b) => (a.city > b.city ? 1 : -1));
        return (this.cities = sortCities);
      });
  },
  methods: {
    getFilter(item) {
      this.filter = item;
    },
    getDataWeather(item) {
      this.weather = item;
    },
  },
  computed: {
    filteredCities() {
      return this.cities.filter((el) => {
        return el.city.toLowerCase().indexOf(this.filter.toLowerCase()) !== -1;
      });
    },
    filteredFavoriteCities() {
      return this.favoriteCities.filter((city) => {
        return Object.keys(this.weather).every((key) => {
          return city.weather[key] === this.weather[key];
        });
      });
    },
  },
};
</script>

<style src="./assets/css/style.css"></style>
