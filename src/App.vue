<template>
  <div id="app">

   <nav>
      <router-link to = "/">Home</router-link>
      <router-link to = "/about">About</router-link>
   </nav>

   <transition 
          name = "router-anim" 
          mode = "out-in"
          enter-active-class="animated fadeInDown" 
          leave-active-class="animated fadeOutDown">
      <router-view />
   </transition>
   
  </div>
</template>

<script>
  import Skills from './components/Skills.vue'

  export default {
    name: 'app',
    components: {
      Skills
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');
  @import 'https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.0/animate.min.css';
  body{
    background-color:#EEEEEE;
    font-family: 'Monserrat', sans-serif;
    display: flex;
    justify-content: center;
    padding-top:50px;
  }

  body, html{
    margin:0;
    height:100%;
  }

  #app {
    width:50%;
  }

  nav {
    padding: 20px 20px 20px 0;
  }
  nav a {
    padding:10px;
    text-decoration: none;
    background:#fff;
    border-radius: 3px;
    color:rgb(0,110,255);
    font-weight: bold;
    margin-right: 15px;
  }
  /* .routes-enter-active, .routes-leave-active{
    transition:opacity .5s;
  }
  .routes-enter, .routes-leave-active{
    opacity: 0
  } */

</style>