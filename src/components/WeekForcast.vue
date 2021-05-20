<template>
  <div class="weekForcast">
    <p class="weekForcast__day">{{ format(day) }}</p>
    <p class="weekForcast__img"><img v-bind:src="imgUrl" alt="" /></p>
    <p class="weekForcast__degree">{{ minT }} <sup>o</sup> <span class="weekForcast--degree">{{ maxT }}<sup>o</sup></span></p>
    
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "WeekForcast",
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
.weekForcast {
  width:20%;
  border-right: 1px dotted rgb(80, 93, 100);
  box-sizing: border-box;
  background: rgb(36, 40, 42);
  color: azure;
}
.weekForcast__img {
  width: 100%;
}
.weekForcast__day{
  text-transform: uppercase;
  font-size: 1.5rem;
}
.weekForcast__degree{
  font-size: 1.5rem;
  font-weight: bold;
  color: rgb(247, 197, 35);
}
.weekForcast--degree{
  color: white;
}
@media (max-width: 675px) {
  .weekForcast {
    border: none;
    text-align: center;
  }
}
</style>
