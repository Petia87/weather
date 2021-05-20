<template>
  <div class="pageMain">
    <DropDown @selectedCity="onSelectedCity" />
    <CityTime v-bind:city="city" v-bind:country="country" />
    <CurrentForcast
      v-bind:temp="temp"
      v-bind:description="description"
      v-bind:iconCurrent="iconCurrent"
    />

    <div v-if="arr.length > 0" class="pageMain__weekForcast">
      <WeekForcast
        v-for="el in objArr"
        :key="el"
        v-bind:day="el.datetime"
        v-bind:icon="el.weather.icon"
        v-bind:minT="el.app_min_temp"
        v-bind:maxT="el.app_max_temp"
      />
    </div>
  </div>
</template>

<script>
import moment from "moment";
import DropDown from "./DropDown.vue";
import CityTime from "./CityTime.vue";
import CurrentForcast from "./CurrentForcast.vue";
import WeekForcast from "./WeekForcast.vue";

export default {
  name: "ThePage",

  components: {
    DropDown,
    CityTime,
    CurrentForcast,
    WeekForcast,
  },

  data: function () {
    return {
      city: "",
      country: "",
      selectedCities: [],
      temp: 0,
      description: "",
      date: "",
      iconBig: "",
      objArr: [],
      arr: [],
    };
  },
  created() {
    this.day = this.getDay();
  },
  methods: {
    format(dateString) {
      return moment(dateString).format("dddd");
    },
    getDay() {
      return moment().format("dd");
    },

    /**
     * Selected city
     */
    onSelectedCity(selectedCities) {
      this.selectedCities = selectedCities;
      this.city = selectedCities.cityName;
      this.country = selectedCities.countryName;
      this.getCurrentWeatherResponse();
      this.getDailyWeatherResponse();
    },

    /**
     * Get current weather response
     */
    getCurrentWeatherResponse() {
      fetch(
        `https://api.weatherbit.io/v2.0/current?key=79bb1bf8c6394da3a3760df1b26bd53b&city=${this.selectedCities.cityName}&country=${this.selectedCities.countryCode}`
      )
        .then((response) => {
          return response.json();
        })
        .then((data) => {
          this.currentRequest = data.data;
          let dataObj = this.findCity();
          this.setProperties(dataObj);
        })
        .catch(() => {});
    },

    /**
     * Find the city wiht selected name and compare with response
     */
    findCity() {
      let dataObj = this.currentRequest.find((obj) => {
        return obj.city_name === this.selectedCities.cityName;
      });
      return dataObj;
    },
    /**
     * Set up properties from the request data
     */
    setProperties(dataObj) {
      this.temp = dataObj.temp;
      this.description = dataObj.weather.description;
      this.iconBig = dataObj.weather.icon;
    },
    /**
     * Get dayly weather response
     */
    getDailyWeatherResponse() {
      this.objArr = [];
      fetch(
        `https://api.weatherbit.io/v2.0/forecast/daily?key=79bb1bf8c6394da3a3760df1b26bd53b&city=${this.selectedCities.cityName}&country=${this.selectedCities.countryCode}`
      )
        .then((response) => {
          return response.json();
        })

        .then((result) => {
          if (result.city_name === this.selectedCities.cityName) {
            this.arr = result.data;

            for (let i = 0; i < this.arr.length; i++) {
              const el = this.arr[i];
              this.objArr.push(el);
              if (this.objArr.length > 4) {
                break;
              }
            }
          }
        })

        .catch(() => {});
    },
    /* resize() {
      this.objArr = [];
    },*/
  },
};
</script>

<style>
.pageMain {
  background: rgb(27, 31, 33);
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.pageMain__weekForcast {
  display: flex;
  flex-direction: row;
  background: rgb(36, 40, 42);
  width: 90%;
  box-sizing: border-box;
  margin: 3%;
}
@media (max-width: 675px) {
  .pageMain__weekForcast {
    flex-direction: column;
    border: none;
  }
}
</style>
