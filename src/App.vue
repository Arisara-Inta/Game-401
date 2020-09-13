<template>
  <div id="app">
    <img class="rounded-circle" src="./assets/fairy.png" width="20%" />
    <HelloWorld msg="CS313_GAME" />
    <h6 class="text-light">RANDOM CHARACTER</h6>
    <br>
    <div>
      <botton />
    </div>
    <footer class="my-0 pt-0 text-muted text-center text-small">
        <p class="mb-0">MJU6104101401@mju.ac.th</p>
    </footer>
  </div>
</template>
<script>
import HelloWorld from "./components/HelloWorld.vue";
import botton from "./components/botton.vue";
export default {
  name: "App",
  components: {
    HelloWorld,
    botton,
  },
};
</script>
<style>
#app {
  background-image: url(https://plainbackground.com/plain1024/fcc2be.png);
  height: 100%;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  position: relative;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
}

</style>
