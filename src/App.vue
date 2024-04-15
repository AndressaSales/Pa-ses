<template>
  <div>
   <CountriesPaises/>
  </div>
</template>
<script>
import CountriesPaises from './components/CountriesPaises.vue'
export default{
  name: "App",
  components:{
   CountriesPaises
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  body{
    background-image: url('./img/globo.jpg');
    background-size: cover;
  }
</style>