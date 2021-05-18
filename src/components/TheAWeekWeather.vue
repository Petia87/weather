<template>
<div class="thirt">
  <p class="today">{{day}}</p>
  <p class="sunfa">{{icon}}</p>
  <p class="degreem">{{degree}}</p>
</div>



</template>

<script>
export default {
  name: 'TheAWeekWeather',
  props: ["day","icon","degree"],
}
</script>


<style scoped>
.thirt{
  width: 17%;
  border: 1px solid red;
  display: inline-block;
  background:rgb(36, 40, 42) ;
  color: azure;
}
</style>
