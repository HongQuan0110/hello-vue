<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Menu />
    <input type="text" v-model="name" />
    {{name}}
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Menu from './components/Menu.vue'

export default {
  name: 'App',
  data() {
    return {
      name: "Vue"
    }
  },
  components: {
    HelloWorld,
    Menu
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
  margin-top: 60px;
}
</style>
