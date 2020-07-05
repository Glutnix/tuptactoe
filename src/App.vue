<template>
  <div id="app">
    <TupTicTacToe/>
  </div>
</template>

<script>
import TupTicTacToe from "./components/TupTicTacToe";

export default {
  name: "App",
  components: {
    TupTicTacToe
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
