<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <button @click="indexGitapi()">Click me</button>
    {{ vuejs.stargazers_count }}
    {{ vuejs.watchers }}
    {{ vuejs.watchers_count }}
    <button @click="indexAngularjs()">Click me</button>
    {{ angularjs.stargazers_count }}
    {{ angularjs.watchers }}
    {{ angularjs.watchers_count }}
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      vuejs: {},
      angularjs: {},
    };
  },
  created: function () {},
  methods: {
    indexGitapi: function () {
      axios.get("/repos/vuejs/vue").then((response) => {
        console.log("github", response.data);
        this.vuejs = response.data;
      });
    },
    indexAngularjs: function () {
      axios.get("/repos/angular/angular.js").then((response) => {
        console.log("github", response.data);
        this.angularjs = response.data;
      });
    },
  },
};
</script>
