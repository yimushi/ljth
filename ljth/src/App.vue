<template>
  <div id="app">
    <div class="header gradient">
      <img src="./assets/ljth_logo.png" alt="">
    </div>
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style>

html,body{
  padding:0;
  margin: 0;
  width: 100%;
  height: 100%;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color:#000;
  width: 100%;
  height: 100%;
}
.header{
  width: 100%;
  height: 100px;
  text-align: right;
  padding-right: 30px;
}
 /* .gradient{
    background: -moz-linear-gradient(top, #000000 0%, #ffffff 100%);
    background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#000000), color-stop(100%,#ffffff));
    background: -webkit-linear-gradient(top, #000000 0%,#ffffff 100%);
    background: -o-linear-gradient(top, #000000 0%,#ffffff 100%);
    background: -ms-linear-gradient(top, #000000 0%,#ffffff 100%);
    background: linear-gradient(to left, #c42c2c 0%,#efdada 100%);
}  */
.header img{
  height: 100%;
  width: 400px;
  margin-right: 20px;
}
</style>
