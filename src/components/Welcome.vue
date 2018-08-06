<template>
    <div>
        <h1>Welcome to the Shopping List App</h1>
        <br><br>
        <p>Give your Shopping List a name</p>

        <form>
            <input type="text" placeholder="Enter the name of your shopping list" v-model="listName">
            <button class="name__button" @click.prevent="addItem">
          Enter
        </button>            
        </form>
        <br><br><br>
        <nav>      
            <router-link to="/">Add Items to Shopping List</router-link>
        </nav>
        {{ listName }}
    </div>
</template>

<script>
export default {
      data() {
        return {
        listName: ''
    }
  }
}
</script>


<style>
  input {   
    width: 300px;
    padding: 10px;
    font-size: 1em;
    background-color: lightgrey;
    color: #687F7F;
  }

  .name__button {
  width: 130px;
  font-size: 1em;
  background: rgb(3, 119, 65);
  border: none;
  color: white;
  cursor: pointer;
  display: inline-block;
  vertical-align: middle;
  line-height: 1.1;
  margin-left: 0px;
  padding: 10px;
}
</style>




