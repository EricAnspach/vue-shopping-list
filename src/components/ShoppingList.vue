<template>
  <div class="hello">
    <div class="holder">

      <ul>
        <li v-for="(data, index) in listItems" :key='index'>{{ data.listItem }}  {{ data.sku }}  {{ data.price }}</li>
      </ul>

      <br><br>

      <form @submit.prevent="addItem">
        <input type="text" placeholder="Enter an item" v-model="listItem">
        <!--
        <input type="text" placeholder="Enter a sku" v-model="sku">
        <input type="text" placeholder="Enter a price" v-model="price"> -->
        <button class="add__button"><i class="ion-ios-checkmark-outline"></i></button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ShoppingList',
  data() {
    return {
      listItem: '',
      listItems: [
        { "listItem": "Milk", "sku": 123, "price": 3 }
      ]
    }
    var input = getInput();

  },
  methods: {
    getInput() {
      return {
        listItem: this.listItem,
        sku: this.sku,
        price: this.price
      }
    },
    addItem() {
      this.listItems.push(input);
      /*
      this.listItem = '';
      this.sku = '';
      this.price = ''; */
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.holder {
    background: rgb(188, 247, 111);
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 10px;
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
    width: calc(100% - 20px);
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
    font-size: 35px;
    background: none;
    border: none;
    color: rgb(3, 119, 65);
    cursor: pointer;
    display: inline-block;
    vertical-align: middle;
    line-height: 1.1;
    margin-left: 10px;
}
</style>
