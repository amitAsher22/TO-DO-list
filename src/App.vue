<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
  <TODo/>

  </div>
</template>

<script>

import TODo from "@/components/TODo";

export default {
  name: 'App',
  components: {
    TODo
   
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
  margin-top: 30px;
}
</style>
