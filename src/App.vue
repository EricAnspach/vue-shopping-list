<template>
  <div id="app">
    <ShoppingList />   
  </div>
</template>

<script>
import ShoppingList from './components/ShoppingList.vue'

export default {
  name: 'app',
  components: {
    ShoppingList
  }

}
</script>

<style>
 @import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');
 @import url('http://code.ionicframework.com/ionicons/2.0.1/css/ionicons.min.css');

body {
  background-color: rgb(249, 244, 98);
  font-family: 'Montserrat', sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  padding-top: 50px;
}
body, html {
  margin: 0;
  height: 100%;
}
#app {
    width: 600px;
}
</style>

