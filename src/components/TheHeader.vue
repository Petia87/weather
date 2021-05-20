<template>
  <div class="header">
    <img class="header__vue" src="./logo.png" alt="" />
    <h4 class="header__title">What's the weather like in...?</h4>
  </div>
</template>

<script>
export default {
  name: "TheHeader",
  props: {},
};
</script>


<style scoped>
.header {
  background: black;
  border-bottom: 0.3rem solid rgb(104, 104, 105);
  color: rgb(208, 209, 210);
  font: weight;
  padding: 1rem;
  display: flex;
  align-items: flex-start;
}
.header__vue {
  width: 5%;
  padding: 0 0.5rem;
}
.header__title {
  margin: 0;
}
</style>
