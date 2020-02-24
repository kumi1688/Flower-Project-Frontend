<template>
  <div id="app">
    <header-container></header-container>
    <menu-container></menu-container>
<!--    <h1>{{count}}</h1>-->
<!--    <div style="display: inline-flex">-->
<!--      <h2><button @click="increase">+</button></h2>-->
<!--      <h2><button @click="decrease">-</button></h2>-->
<!--    </div>-->
  </div>
</template>

<script>
import header from "./components/header";
import menu from './components/menu';
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex);

const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {state.count++},
    decrement (state) {state.count--},
  }
});

export default {
  name: 'App',
  components: {
    'header-container' : header,
    'menu-container' : menu,
  },
  computed:{
    count() {
      return store.state.count
    }
  },
  methods:{
    increase() {
      return store.commit('increment');
    },
    decrease(){
      return store.commit('decrement');
    }
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
