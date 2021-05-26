<template>
  <div class="current-forcas">
    <h1 class="current-forcas__title">
      <span class="current-forcas__title_img"
        ><img v-bind:src="imgUrl" alt=""
      /></span>
      {{ temperature }}<sup>o</sup>
    </h1>
    <p class="current-forcas__p">{{ description }}</p>
  </div>
</template>

<script>
export default {
  name: "CurrentForcast",
  props: ["temperature", "description", "iconCurrent"],
  computed: {
    imgUrl() {
      return `https://www.weatherbit.io/static/img/icons/${this.iconCurrent}.png`;
    },
  },
};
</script>


<style scoped>
.current-forcas {
  text-align: center;
  color: white;
}
.current-forcas__title_img {
  width: 30%;
}
.current-forcas__title {
  font-size: 9rem;
  margin-bottom: 0;
  font-weight: 300;
}
.current-forcast__p {
  font-size: 2rem;
  margin-top: 0;
}
</style>
