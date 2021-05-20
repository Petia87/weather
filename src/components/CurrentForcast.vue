<template>
  <div class="currentForcast">
    <h1 class="currentForcast__title">
      <span class="currentForcast__title_img"
        ><img v-bind:src="imgUrl" alt=""
      /></span>
      {{ temp }}<sup>o</sup>
    </h1>
    <p class="currentForcast__p">{{ description }}</p>
  </div>
</template>

<script>
export default {
  name: "CurrentForcast",
  props: ["temp", "description", "iconCurrent"],
  
  computed: {
    imgUrl() {
      return `https://www.weatherbit.io/static/img/icons/${this.iconCurrent}.png`;
    },
  },
};
</script>


<style scoped>
.currentForcast {
  text-align: center;
  color: white;
}
.currentForcast__title_img {
  width: 100%;
}
.currentForcast__title {
  font-size: 9rem;
  margin-bottom: 0;
  font-weight: 300;
}
currentForcast__p {
  font-size: 2rem;
  margin-top: 0;
}
</style>
