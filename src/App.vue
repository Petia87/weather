<template>
<TheHeader/>
  <ThePage/>
 

</template>

<script>
import TheHeader from './components/TheHeader.vue'
import ThePage from './components/ThePage.vue'

export default {
  name: 'App',
  components: {
    TheHeader,
    ThePage
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
} 
 @import url('https://fonts.googleapis.com/css2?family=Newsreader:wght@200&family=Open+Sans:ital,wght@0,300;0,400;0,600;0,700;0,800;1,600;1,700;1,800&display=swap')
*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
   font-family: 'Open Sans', sans-serif;
}

body,div{
  margin: 0;
  padding: 0;
}
</style>


