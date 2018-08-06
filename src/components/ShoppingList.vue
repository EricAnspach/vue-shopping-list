<template>
  <div class="hello">
    <div class="holder">
      <p>{{ listName }}</p>
      <form>
        <input type="text" placeholder="Enter an item" v-model="listItem.item">
        <input type="text" placeholder="Enter a sku" v-model="listItem.sku">
        <input type="text" placeholder="Enter a price" v-model="listItem.price">
        <button class="add__button" @click.prevent="addItem">
          Add an item
        </button>
      </form>

      <br><br>

      <ul>        
          <li v-for="(data, index) in listItems" :key="index">{{ data.item }}, SKU: {{ data.sku }}, Price: {{ data.price }}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>        
      </ul>

      <nav>
        <router-link to="/welcome">Change name of Shopping List</router-link>
      </nav>

    </div>
  </div>
</template>

<script>
export default {
  name: 'ShoppingList',
  data() {
    return {
      listItem: {
        item: '',
        sku: '',
        price: 0 
      },
      listItems: []      
    }    
  },
  methods: {
    addItem() {
      this.listItems.push(
        {item: this.listItem.item, sku: this.listItem.sku, price: this.listItem.price}
        );
      
      this.item = '';
      this.sku = '';
      this.price = '';
    },
    remove(id) {
      this.listItems.splice(id,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";

.holder {
    background: rgb(188, 247, 111);
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1em;
    background-color: white;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }

  input {   
    width: 130px;
    padding: 10px;
    font-size: 1em;
    background-color: lightgrey;
    color: #687F7F;
  }

  .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }



  @keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }


}

i {
  float:right;
  cursor:pointer;
}

.add__button {
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
