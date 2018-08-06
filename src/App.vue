<template>
  <div id="app">
    <router-view></router-view>    
  </div>
</template>

<script>
import ShoppingList from './components/ShoppingList.vue'
import Welcome from './components/Welcome.vue'

export default {
  name: 'app',
  components: {
    ShoppingList,
    Welcome
  },
  data() {
        return {
        listName: ''
    }
  },
  methods: {
      nameList() {
          this.listName = listName;
      }
  }
}
</script>

<style>
 @import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');
 @import url('http://code.ionicframework.com/ionicons/2.0.1/css/ionicons.min.css');

body {
  background-color: rgb(188, 247, 111);
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

nav {
  padding: 20px 20px 20px 0;
}

nav a {
  padding: 10px;
  text-decoration: none;
  background: #fff;
  border-radius: 3px;
  color: rgb(0, 110, 255);
  font-weight: bold;
  margin-right: 15px;
}
</style>

