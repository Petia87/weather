<template>
  <div class="body">
    <DropDown />
    <SityTime />
    <TheAWeather />

    <div class="maintp"></div>
    <TheAWeekWeather />
    <TheAWeekWeather />
    <TheAWeekWeather />
    <TheAWeekWeather />
    <TheAWeekWeather />
  </div>
</template>

<script>
import DropDown from "./DropDown.vue";
import SityTime from "./SityTime.vue";
import TheAWeather from "./TheAWeather.vue";
import TheAWeekWeather from "./TheAWeekWeather.vue";

export default {
  name: "ThePage",
  components: {
    DropDown,
    SityTime,
    TheAWeather,
    TheAWeekWeather,
  },
};
</script>

<style>
.body {
  background:rgb(27, 31, 33);
  padding: 0;
  margin: 0;
}
.maintp{
  display: flex;
  flex-direction:row;
  background: rgb(36, 40, 42);
  width: 95%;
}
</style>
