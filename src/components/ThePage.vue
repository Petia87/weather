<template>
  <div class="page-main">
    <DropDown @SelectedCity="onSelectedCity" />
    <CityTime v-bind:city="city" v-bind:country="country" />
    <CurrentForcast
      v-bind:temperature="temperature"
      v-bind:description="description"
      v-bind:iconCurrent="iconCurrent"
    />

    <div v-if="citiesInformation.length > 0" class="page-main__weekly-forcast">
      <WeeklyForcast
        v-for="el in citiesProperties"
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
import WeeklyForcast from "./WeeklyForcast.vue";

export default {
  name: "ThePage",

  components: {
    DropDown,
    CityTime,
    CurrentForcast,
    WeeklyForcast,
  },

  data: function () {
    return {
      city: "",
      country: "",
      selectedCities: [],
      date: "",
      temperature: 0,
      description: "",
      iconCurrent: "",
      citiesProperties: [],
      citiesInformation: [],
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
      this.selectedCities= selectedCities;
      this.city = selectedCities.cityName;
      this.country = selectedCities.countryName;
      this.getCurrentWeather();
      this.getDailyWeather();
    },

    /**
     * Get current weather response
     */
    getCurrentWeather() {
      fetch(
        `https://api.weatherbit.io/v2.0/current?key=79bb1bf8c6394da3a3760df1b26bd53b&city=${this.selectedCities.cityName}&country=${this.selectedCities.countryCode}`
      )
        .then((response) => {
          return response.json();
        })
        .then((data) => {
          this.currentServer = data.data;
          let citiesServer = this.findCity();
          this.setProperties(citiesServer );
        })
        .catch(() => {});
    },

    /**
     * Find the city 
     */
    findCity() {
      let citiesServer  = this.currentServer.find((cities) => {
        return cities.city_name === this.selectedCities.cityName;
      });
      return citiesServer ;
    },
    /**
     * Set up properties from the cities request
     */
    setProperties(citiesServer ) {
      this.temperature = citiesServer.temp;
      this.description = citiesServer .weather.description;
      this.iconCurrent = citiesServer .weather.icon;
    },
    /**
     * Get dayly weather response
     */
    getDailyWeather() {
      this.reset()
      fetch(
        `https://api.weatherbit.io/v2.0/forecast/daily?key=79bb1bf8c6394da3a3760df1b26bd53b&city=${this.selectedCities.cityName}&country=${this.selectedCities.countryCode}`
      )
        .then((response) => {
          return response.json();
        })

        .then((result) => {
          if (result.city_name === this.selectedCities.cityName) {
            this.citiesInformation = result.data;

            for (let i = 0; i < this.citiesInformation.length; i++) {
              const el = this.citiesInformation[i];
              this.citiesProperties.push(el);
              if (this.citiesProperties.length > 4) {
                break;
              }
            }
          }
        })

        .catch(() => {});
    },
    reset() {
      this.citiesProperties = [];
    },
  },
};
</script>

<style>
.page-main {
  background: rgb(27, 31, 33);
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.page-main__weekly-forcast {
  display: flex;
  flex-direction: row;
  background: rgb(36, 40, 42);
  width: 90%;
  box-sizing: border-box;
  margin: 3%;
}
@media (max-width: 675px) {
  .page-main__week-forcast {
    flex-direction: column;
    border: none;
  }
}
</style>
