<template>
  <div class="body">
    <DropDown @selectedCity="onSelectedCity"/>
    <SityTime v-bind:city="city" v-bind:country ="country" />
    <TheAWeather />

    <div class="maintp"></div>
    <TheAWeekWeather class="greyBox" day="today" icon="icon" degree="degree" />
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
   data: function () {
    return {
      city:"",
     country:"",

    };
  },
  methods:{
    onSelectedCity(cityArr){// "selectedSity", this.selectedSity,this.cityArr
      console.log(cityArr); //ne stava
     //this.city=city
      //this.country=country

    }
  }
 
};

</script>

<style>
.body {
  background: rgb(27, 31, 33);
  padding: 0;
  margin: 0;
}
.maintp {
  display: flex;
  flex-direction: row;
  background: rgb(36, 40, 42);
  width: 95%;
}
/*v-bind: today  /*day="today"
    v-bind:icon="icon" 
    v-bind:degree="degree"/>*/
</style>
