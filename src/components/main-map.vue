<template>
  <l-map
    v-if="showMap"
    style="height: 100%"
    :zoom="zoom"
    :center="center"
    :bounds="bounds"
  >
    <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
    <l-marker
      v-for="(item, idx) in markerLatLng"
      :key="idx"
      :lat-lng="item"
      :icon="icon"
    >
    </l-marker>
  </l-map>
</template>

<script>
import { LMap, LTileLayer, LMarker } from "vue2-leaflet";
import { icon } from "leaflet";

export default {
  name: "main-map",
  props: {
    favorCity: Array,
  },
  components: {
    LMap,
    LTileLayer,
    LMarker,
  },
  data() {
    return {
      url: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      attribution:
        '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      zoom: 10,
      center: [51.505, -0.159],
      markerLatLng: [],
      bounds: [
        [52.2978, 104.2964],
        [52.2978, 104.2964],
      ],
      icon: icon({
        iconUrl: "/assets/img/icon/marker.svg",
        iconSize: [32, 37],
        iconAnchor: [16, 37],
      }),
      iconSize: 64,
      showMap: false,
    };
  },
  mounted() {
    fetch("https://ipinfo.io/json?token=c837035fffa842")
      .then((responce) => responce.json())
      .then((data) => {
        this.center = data.loc.split(",");
        this.showMap = true;
      })
      .catch((error) => console.log(error));
  },
  methods: {},
  computed: {
    dynamicSize() {
      return [this.iconSize, this.iconSize * 1.15];
    },
    dynamicAnchor() {
      return [this.iconSize / 2, this.iconSize * 1.15];
    },
  },
  watch: {
    favorCity() {
      const intermediateCities = [];
      this.favorCity.forEach((item) => {
        const currentCities = [];
        currentCities[0] = item.coordinates.latitude;
        currentCities[1] = item.coordinates.longitude;
        intermediateCities.push(currentCities);
      });
      this.markerLatLng = intermediateCities;
      this.bounds = intermediateCities;
    },
  },
};
</script>

<style></style>
