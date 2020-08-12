<template>
<div id="app">
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App" />
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import {
  API
} from 'aws-amplify';

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    getPrograms() {
      const apiName = 'keyserverAPI';
      const path = '/program';
      const myInit = { // OPTIONAL
        // headers: {}, // OPTIONAL
        // response: true, // OPTIONAL (return the entire Axios response object instead of only response.data)
        // queryStringParameters: {  // OPTIONAL
        //     name: 'param',
        // },
      };

      API
        .get(apiName, path, myInit)
        .then(response => {
          console.log('program response');
          console.log(response);
        })
        .catch(error => {
          console.log('error response from api');
          console.log(error.response);
        });
    }
  },
  mounted: function() {
    this.getPrograms();
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
