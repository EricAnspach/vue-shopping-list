<template>
  <div class="hello">
    <div class="holder">
      
      <div>
        <h1 class="page_title">The Shopping List App</h1>

      </div>
      <div>
        <form v-if="!isNamed">
            <input class="name_input" type="text" placeholder="Enter the name of your shopping list" v-model="listName">
            <button class="name__button" @click.prevent="listNamed">
                Enter
            </button>                       
        </form>        
      </div>

      <div v-if="isNamed">
        <h1>{{ listName }}</h1> 
        <form>
          <input type="text" placeholder="Enter an item" v-model="listItem.item">
          <input type="text" placeholder="Enter a sku" v-model="listItem.sku" 
            v-validate="'digits:6'" name="sku">
          <input type="text" placeholder="Enter a price" v-model="listItem.price" 
            v-validate="'numeric'" data-vv-as="price" name="numeric_field">
          <button class="add__button" @click.prevent="addItem">
            Add an item
          </button>
          <p class="alert" v-if="errors.has('sku')">{{ errors.first('sku') }}</p>
          <p class="alert" v-if="errors.has('numeric_field')">{{ errors.first('numeric_field') }}</p>
        </form>

        <br><br>

        <ul>        
            <li v-for="(data, index) in listItems" :key="index">{{ data.item }}, SKU: {{ data.sku }}, Price: {{ data.price }}
              <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
            </li>        
        </ul>
        <hr>
        <p></p>
        <p>{{ total }}</p>

        <br><br>
        <button class="change__button" v-on:click="clearName">Change name of Shopping List</button>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'ShoppingList',
  data() {
    return {
      listName: '',
      listItem: {
        item: '',
        sku: '',
        price: ''
      },
      listItems: [],
      isNamed: false,
      total: 0,
      addPrice: 0,
      removePrice: 0
    }    
  },
  methods: {
    addItem() {
      this.listItems.push(
        {item: this.listItem.item, sku: this.listItem.sku, price: this.listItem.price}
        );
      

      this.addPrice = parseInt(this.listItem.price, 10);
      console.log(this.addPrice);
      this.total = this.total += this.addPrice;
      this.listItem.item = '';
      this.listItem.sku = '';
      this.listItem.price = '';
    },
    remove(id) {
      removePrice = this.listItems[id.price];
      this.listItems.splice(id,1);
      this.total = this.total -= this.removePrice;
    },
    listNamed() {
      this.isNamed = true;
    },
    clearName() {
      this.isNamed = false;
      this.listName = '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";

.holder {
  background: rgb(249, 244, 98);
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
  color: black;
}

p {
  text-align:center;
  padding: 30px 0;
  color: gray;
}

.alert {
  padding: 0px;
  color: red;
}

.container {
  box-shadow: 0px 0px 40px lightgray;
}

.page_title {
  font-size: 3em;
}

input {   
  width: 130px;
  padding: 10px;
  font-size: 1em;
  background-color: lightgrey;
  color: black;
}

.name_input {   
  width: 300px;
  padding: 10px;
  font-size: 1em;
  background-color: lightgrey;
  color: black;
}

i {
  float:right;
  cursor:pointer;
}

.add__button {
  width: 130px;
  font-size: 1em;
  background: rgb(243, 139, 38);
  border: none;
  color: white;
  cursor: pointer;
  display: inline-block;
  vertical-align: middle;
  line-height: 1.1;
  margin-left: 0px;
  padding: 10px;
}

.name__button {
  width: 130px;
  font-size: 1em;
  background: rgb(243, 139, 38);
  border: none;
  color: white;
  cursor: pointer;
  display: inline-block;
  vertical-align: middle;
  line-height: 1.1;
  margin-left: 0px;
  padding: 10px;
}

.change__button {
  width: 600px;
  font-size: 1em;
  background: rgb(243, 139, 38);
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
