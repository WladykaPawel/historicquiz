<template>
  <div class="main">
      <HelloWorld msg="Sprawdź swoją wiedzę Historyczną"/>
      <div class="line"></div>
      <h6 class="podpis">Created by <a href="https://github.com/WladykaPawel">@WladykaPawel</a></h6>
  </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
}
.main
{
  background: url("./assets/44.gif");
  background-size: cover;
  margin: 0;
  padding-bottom: 50px;
  min-height: 2000px;
  padding-top: 50px;
  font-family: "fantasy";
}
.line
{
  position: absolute;
  top: 1950px;
  left: 20px;
  height: 5px;
  width: 90vw;
  background-color: gray;
  margin-left: 4vw;
}
.podpis
{
  position: absolute;
  top: 1955px;
  left: 45vw
}

</style>
