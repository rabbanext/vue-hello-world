<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  
  <div v-for="item, index in info" :key="index">
    {{ item }}
    <a :href="item.url">{{ item.name }}</a>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      info: null
    }
  },
  components: {
    HelloWorld
  },
  mounted() {
    axios
      .get('https://pokeapi.co/api/v2/pokemon/')
      .then(response => {
        console.log(response)
        this.info=response.data.results
      })
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
