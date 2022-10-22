<template>
  <Todolist msg="To-do list"/>
</template>

<script>
import Todolist from './components/Todolist.vue';


export default {
  name: 'App',
  components: {
    Todolist
}
}
</script>

<style>
html{
    height:100%;
} 
body {
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
