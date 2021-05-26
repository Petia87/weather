<template>
  <div class="city-time">
    <div class="city-time__main">
      <h2 class="city-time__main__title">
        <span class="city-time__main__title__span"
          ><i class="fas fa-map-marker-alt"></i
        ></span>
        {{ city }}
        <i
          ><small> ({{ country }}) </small></i
        >
      </h2>
      <div class="city-time__main__current-date">{{ currentDate }}</div>
    </div>
    <div class="city-time__temp">
      <button class="city-time__temp__c"><sup>o</sup> C</button>
      <button class="city-time__temp__f"><sup>o</sup> F</button>
    </div>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "CityTime",
  props: ["city", "country"],

  data: function () {
    return {
      currentDate: "",
    };
  },
  created() {
    this.currentDate = this.getCurrentDateTime();
  },
  methods: {
    getCurrentDateTime() {
      return moment().format("dddd, MMM DD - HH:mm");
    },

    getNow() {
      const current = new Date();
      const date = `${current.getDay()}${[
        current.getMonth() + 1,
      ]} ${current.getDate()} ${current.getFullYear()}`;
      const time = `${current.getHours()}:${current.getMinutes()}:${current.getSeconds()}`;
      const dateTime = date + " " + time;
      this.currentDate = dateTime;
    },
  },
};
</script>

<style scoped>
.city-time{
  display: flex;
  flex-direction: row;
}
.city-time__main {
  width: 70%;
  text-align: left;
  color: white;
  border-color: yellow;
  padding-left: 2rem;
}
.city-time__temp {
  width: 30%;
  padding-top: 5rem;
}
.fa-map-marker-alt {
  color: rgb(251, 189, 8);
}
.city-time__main__title__span {
  margin-bottom: 0;
}
.city-time__main__current-date {
  padding-left: 1.2rem;
  font-size: 1rem;
}
.city-time__main__title {
  margin-bottom: 0.3rem;
}
.city-time__temp__c,
.city-time__temp__f {
  border: none;
  background-color: rgb(202, 203, 205);
  color: black;
  padding: 0.3rem 0.8rem;
}
.city-time__temp__c {
  border-top-left-radius: 10%;
  border-bottom-left-radius: 10%;
}
.city-time__temp__f {
  border-top-right-radius: 10%;
  border-bottom-right-radius: 10%;
}
.city-time__temp__c,
.city-time__temp__f:hover {
  border: none;
  background-color: rgb(14, 164, 50);
  color: rgb(202, 203, 205);
}
</style>
