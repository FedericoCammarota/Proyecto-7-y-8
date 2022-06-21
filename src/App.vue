<template>
  <div class="container-fluid mt-3">
    <div class="jumbotron">
      <h1>Ejericios 7 y 8</h1>
      <br>
      
      <Navbar />
      <router-view></router-view>

    </div> 
  </div>
</template>

<script>


import Navbar from './components/Navbar.vue'

export default {
  name: 'App',
  components: {
   
    Navbar
  }
}
</script>

<style>
  h1 {
    color: black;    
  }
  .jumbotron{
    border: black solid 3px;
    border-radius: 10px;
    /* Permalink - use to edit and share this gradient: https://colorzilla.com/gradient-editor/#959595+0,0d0d0d+46,010101+50,0a0a0a+53,4e4e4e+76,383838+87,1b1b1b+100;Black+Gloss+Pipe */
background: #959595; /* Old browsers */
background: -moz-linear-gradient(-45deg,  #959595 0%, #0d0d0d 46%, #010101 50%, #0a0a0a 53%, #4e4e4e 76%, #383838 87%, #1b1b1b 100%); /* FF3.6-15 */
background: -webkit-linear-gradient(-45deg,  #959595 0%,#0d0d0d 46%,#010101 50%,#0a0a0a 53%,#4e4e4e 76%,#383838 87%,#1b1b1b 100%); /* Chrome10-25,Safari5.1-6 */
background: linear-gradient(135deg,  #959595 0%,#0d0d0d 46%,#010101 50%,#0a0a0a 53%,#4e4e4e 76%,#383838 87%,#1b1b1b 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#959595', endColorstr='#1b1b1b',GradientType=1 ); /* IE6-9 fallback on horizontal gradient */

  }

</style>
