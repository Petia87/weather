<template>
  <select @change="onChange" class="dropdown">
    <option v-for="city in cities" :key="city" v-bind:value="city.cityName">
      {{ city.cityName }}
    </option>
  </select>
</template>

<script>
import { countryList } from "../data/countries1.js";

export default {
  name: "DropDown",
  emits: ["selectedCity"],
  props: {},

  data: function () {
    return {
      cities: [],
    };
  },

/**
 * Create cities 
 */
  mounted() {
    for (let i = 0; i < countryList.length; i++) {
      let country = countryList[i];
      for (let j = 0; j < country.cities.length; j++) {
        let city = country.cities[j];
        this.cities.push({
          cityName: city.name,
          countryName: country.name,
          countryCode: country.iso2,
        });
      }
    }
  },
  /**
   * 
   */
  methods: {
    onChange(eventInfo) {
      let selectedCity = eventInfo.target.value;
      let selectedCities = this.cities.find((cities) => {
        return cities.cityName === selectedCity;
      });
      this.$emit("selectedCity", selectedCities);
    },
  },
};
</script>



<style scoped>
.dropdown {
  width: 80%;
  padding: 0.5rem;
  border-top-left-radius: 0.3rem;
  border-top-right-radius: 0.3rem;
  margin: 0.5rem;
}
</style>
