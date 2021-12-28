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
            <div class="small-card small-card--shadow">
              <span class="small-card__city"> Чебоксары </span>
              <span class="small-card__temperature">+17°</span>
              <span class="icon icon--strips-small"></span>
            </div>
            <div class="small-card small-card--empty"></div>
            <smallCard
              v-bind:city="item"
              v-for="(item, idx) in filteredCities"
              v-bind:key="idx"
            ></smallCard>
          </div>
          <div class="weather-content__big-cards">
            <div class="weather-content__help">
              Перетащите сюда города, погода в которых вам интересна
            </div>
            <bigCard></bigCard>
            <bigCard></bigCard>
            <div class="big-card big-card--shadow">
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
            <div class="big-card big-card--empty"></div>
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

export default {
  name: "App",
  components: {
    smallCard,
    bigCard,
    mainMap,
    sortBtn,
    filterCity,
    filterweather,
  },
  data() {
    return {
      cities: [],
      filter: "",
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
