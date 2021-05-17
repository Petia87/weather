<template>
<div class="first">
  <div class="citytime">
  <h2>
    <span><i class="fas fa-map-marker-alt"></i></span>
    city(country)
  </h2>
<div>{{ currentDate }}</div>
 
</div>
 <div class="degree">
      <button>C</button>
      <button>F</button>
    </div>

</div>


</template>

<script>
import moment from "moment"
export default {
  name: 'SityTime',
  props: {
   
  },
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
      return moment().format("dddd, MMM d- HH:mm");
    },
   
    getNow: function () {
      const current = new Date();
      const date = `${current.getDay()}${[current.getMonth() + 1]} ${current.getDate()} ${current.getFullYear()}`;
      const time = `${current.getHours()}:${current.getMinutes()}:${current.getSeconds()}`;
      const dateTime = date + " " + time;
      this.currentDate = dateTime
    },
  },
};
</script>



<style scoped>
.first{
  display: flex;
  flex-direction: row;
}
.citytime{
  width: 70%;
  text-align: left;
  color: white;
 border-color: yellow;
 padding-left: 2rem;
}
.degree{
  width:30%;
  padding-top:5rem;
 
}
</style>
