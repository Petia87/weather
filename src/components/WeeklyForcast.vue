<template>
  <div class="weekly-forcast">
    <p class="weekly-forcast__day">{{ format(day) }}</p>
    <p class="weekly-forcast__img"><img v-bind:src="imgUrl" alt="" /></p>
    <p class="weekly-forcast__degree">{{ minT }} <sup>o</sup> <span class="weekly-forcast--degree">{{ maxT }}<sup>o</sup></span></p>
    
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "WeeklyForcast",
  props: ["day", "icon", "minT", "maxT"],

  computed: {
    imgUrl() {
      return `https://www.weatherbit.io/static/img/icons/${this.icon}.png`;
    },
  },
  methods: {
    format(dateString) {
      return moment(dateString).format("dddd");
    },
  },
};

</script>

<style scoped>
.weekly-forcast {
  width:20%;
  border-right: 1px dotted rgb(80, 93, 100);
  box-sizing: border-box;
  background: rgb(36, 40, 42);
  color: azure;
}
.weekly-forcast__img {
  width: 100%;
}
.weekly-forcast__day{
  text-transform: uppercase;
  font-size: 1.5rem;
}
.weekly-forcast__degree{
  font-size: 1.5rem;
  font-weight: bold;
  color: rgb(247, 197, 35);
}
.weekly-forcast--degree{
  color: white;
}
@media (max-width: 675px) {
  .weekly-forcast {
    border: none;
    text-align: center;
  }
}
</style>
