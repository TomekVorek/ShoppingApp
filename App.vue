<template>
  <div id="wrapper">
    <h1>ShoppingApp - aplikacja do wakacyjnych zakupów :)</h1>
    <div id="input-container">
      <table>
        <tr>
          <td>
            <label for="item">Wpisz produkt </label>
            <input name="item" type="text" placeholder="Co chcesz kupić?" v-model="newTitle">
          </td>
          <td>
            <label for="quantity">Ile potrzebujesz? </label>
            <input name="quantity" type="text" placeholder="Ile sztuk?" v-model="newQuantity"> 
          </td>
          <td>
             <button @click="addItem">Dodaj do listy</button>
          </td>
        </tr>
      </table>
       
     
    </div>
    <div id="list-container">
      <div class="item">
      <table>
        <div>
        <tr>
          <td>Produkt </td>
          <td>Ilość [szt.] </td>
          <td>Status</td>
        </tr>
        <tr v-for = "item in items" v-bind:key="item.id" v-bind:class="{completed: item.completed}">
    
          <td><h4>{{item.title}}</h4></td>
          <td><h4>{{item.quantity}}</h4></td>
          <td><button v-if="!item.completed" @click="removeItem(item.id)"><img src="../public/shopping-cart.png" alt=""></button>
          <img v-if="item.completed" src="../public/correct.png" alt="correct">
          <button @click="deleteItem(item.id)"><img src="../public/trash.png" alt=""></button>
          
        </td>
        </tr>
        </div>
      </table>      
      </div>
    </div>
  </div>
</template>

<script>  
export default {
  data() {
    return {
      newTitle: '',
      newQuantity: '',
      items: [
        
      ]
    }
  },
  methods: {
    addItem() {
      this.items.push({title: this.newTitle, quantity: this.newQuantity, completed: false, id: Math.random()})
      this.newTitle = ''
      this.newQuantity = ''
    },
    removeItem(id) {
      const index = this.items.findIndex(el => el.id === id)
      this.items[index].completed = 'true'
    },
    deleteItem(id){
      const index = this.items.findIndex(el => el.id === id)
      this.items.splice(index, 1)
    }}}
  
</script>

