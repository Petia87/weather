<template>
  <div class="cityTime">
    <div class="cityTime__main">
      <h2 class="cityTime__main__title">
        <span class="cityTime__main__title__span"
          ><i class="fas fa-map-marker-alt"></i
        ></span>
        {{ city }}
        <i
          ><small> ({{ country }}) </small></i
        >
      </h2>
      <div class="cityTime__main__currentDate">{{ currentDate }}</div>
    </div>
    <div class="cityTime__temp">
      <button class="cityTime__temp__c"><sup>o</sup> C</button>
      <button class="cityTime__temp__f"><sup>o</sup> F</button>
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

    getNow: function () {
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
.cityTime {
  display: flex;
  flex-direction: row;
}
.cityTime__main {
  width: 70%;
  text-align: left;
  color: white;
  border-color: yellow;
  padding-left: 2rem;
}
.cityTime__temp {
  width: 30%;
  padding-top: 5rem;
}
.fa-map-marker-alt {
  color: rgb(251, 189, 8);
}
.cityTime__main__title__span {
  margin-bottom: 0;
}
.cityTime__main__currentDate {
  padding-left: 1.2rem;
  font-size: 1rem;
}
.cityTime__main__title {
  margin-bottom: 0.3rem;
}
.cityTime__temp__c,
.cityTime__temp__f {
  border: none;
  background-color: rgb(202, 203, 205);
  color: black;
  padding: 0.3rem 0.8rem;
}
.cityTime__temp__c {
  border-top-left-radius: 10%;
  border-bottom-left-radius: 10%;
}
.cityTime__temp__f {
  border-top-right-radius: 10%;
  border-bottom-right-radius: 10%;
}
.cityTime__temp__c,
.cityTime__temp__f:hover {
  border: none;
  background-color: rgb(14, 164, 50);
  color: rgb(202, 203, 205);
}
</style>
