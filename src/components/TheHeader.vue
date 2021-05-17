<template>
<div class="header">
   <img class="vieicon" src="./logo.png" alt="">
  <h4 class="headerh4" >
   What's the weather like in...?
    </h4>
</div>



</template>

<script>
export default {
  name: 'TheHeader',
  props: {
   
  }
}
</script>


<style scoped>
.header{
  background: black;
  border-bottom: 0.3rem solid rgb(104, 104, 105);
  color: rgb(208, 209, 210);
  font: weight;
 padding: 1rem;
 display: flex;
align-items: flex-start;


    
 
}
.vieicon{
  width: 5%;
  padding: 0 0.5rem;
}
.headerh4{
    margin: 0;
  
}

</style>
