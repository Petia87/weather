<template>
  <select @change="OnChange" class="dropdown">
    <option v-for="city in cityArr" :key="city" v-bind:value="city">
      {{ city.cityName }}
    </option>
  </select>
</template>

<script>
import { countryList } from "../data/countries1.js";

export default {
  name: "DropDown",
  emits: ["cityArr", "selectedCity"],
  props: {},

  data: function () {
    return {
      cityArr: [],
      selectedCity:"",
    };
  },

  mounted() {
    for (let i = 0; i < countryList.length; i++) {
      let country = countryList[i];
      for (let j = 0; j < country.cities.length; j++) {
        let city = country.cities[j];
        this.cityArr.push({
          cityName: city.name,
          countryName: country.name,
          countryCode: country.iso2,
        });
      }
    }
  },
  methods: {
    onChange(eventInfo) {
      this.selectedCity=eventInfo.target.value//find
       this.$emit("selectedCity", this.selectedCity,this.cityArr)
    },
  },
};
</script>



<style scoped>
.city {
  padding: 5rem;
}
</style>
