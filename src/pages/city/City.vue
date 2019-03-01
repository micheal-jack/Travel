<template>
  <div>
    <city-header></city-header>
    <city-list
      :cities="cities"
      :hot="hotCities"
      :letter="letter"
    ></city-list>
    <city-search :cities="cities"></city-search>
    <city-alphabet
      :cities="cities"
      @change="handleLetterChange"
    ></city-alphabet>
  </div>
</template>
<script>
import axios from "axios";
import CityHeader from "./components/header";
import CityList from "./components/list";
import CitySearch from "./components/search";
import CityAlphabet from "./components/Alphabet";
export default {
  name: "City",
  data() {
    return {
      cities: {},
      hotCities: [],
      letter: ""
    };
  },
  components: {
    CityHeader,
    CityList,
    CitySearch,
    CityAlphabet
  },
  mounted() {
    this.getCityInfo();
  },
  methods: {
    getCityInfo() {
      axios.get("/static/mock/city.json").then(this.hanleGetCityInfoSucc);
    },
    hanleGetCityInfoSucc(res) {
      console.log(res);
      res = res.data;
      if (res.ret && res.data) {
        const data = res.data;
        this.cities = data.cities;
        this.hotCities = data.hotCities;
      }
    },
    handleLetterChange(value) {
      this.letter = value;
    }
  }
};
</script>
<style lang="stylus" scoped>
</style>

