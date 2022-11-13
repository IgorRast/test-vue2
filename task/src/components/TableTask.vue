<template>
  <div>
  <v-row class="row">
    <v-text-field @keyup.enter="addLSPrice" class="form1" :rules="rules" id="f1"></v-text-field>
    <v-text-field @keyup.enter="addLSQty" class="form1" :rules="rules" id="f2"></v-text-field>
    <v-text-field @keyup.enter="addLSAm" class="form1" :rules="rules" id="f3"></v-text-field>
    <v-btn @click="showLS" class="btn-1" depressed bottom>
    Button
    </v-btn>
  </v-row>
  <div id="output" >
    <p>Value</p>
  </div>
  <v-card
  elevation="10"
  height="200px"
  outlined
>Москва</v-card>
</div>
</template>

<script>


  export default {
    name: 'TableTask',

    data () {
    return {
      rules: [
        value => value
      ]
    }
   },
   methods: {
    addLSPrice() {
          //     let name = 'Price'
          //     const menuItem = {
          //   name: name,
          //   price: document.getElementById('f1').value,
          // };
              
        // localStorage.setItem(name, JSON.stringify (menuItem) )
        // if (name !='')
        // name=''
        let menuItems = window.localStorage.getItem("Price");
          if (menuItems) {
            menuItems = JSON.parse(menuItems);
          } else {
            menuItems = [];
          }
          let name = 'Price';
          let price = document.getElementById('f1').value;
          const menuItem = {
            name: name,
            price: price,
          };
          menuItems.push(menuItem);
          window.localStorage.setItem("Price", JSON.stringify(menuItems));
          document.getElementById('f1').value = ''            
        },
        addLSQty() {
          let menuItems1 = window.localStorage.getItem("Quantity");
          if (menuItems1) {
            menuItems1 = JSON.parse(menuItems1);
          } else {
            menuItems1 = [];
          }
          let name = 'Quantity';
          let Quantity = document.getElementById('f2').value;
          const menuItem1 = {
            name: name,
            price: Quantity,
          };
          menuItems1.push(menuItem1);
          window.localStorage.setItem("Quantity", JSON.stringify(menuItems1));
          document.getElementById('f2').value = ''
      
         
       
        },
        addLSAm() {
      let name = document.getElementById('f3').value
      localStorage.setItem('Amount', name )
      if (name !='')
      name=''
         
       
        },
    showLS() {
      let output = document.getElementById("output")
      for (let i = 0; i < localStorage.length; i++) {
    let element = document.createElement("p")
    
    element.textContent = localStorage.getItem(localStorage.key(i))
    output.appendChild(element)
}
    }    
        
      }
      
    }
   
  
</script>

<style>
  .form1 {
    width: 50px;
  }
  .row {
    gap: 40px;
    margin-left: 30px;
  }
  .btn-1 {
    margin-top: 15px;
    
  }
  #output {
    margin-bottom: 100px;
  }
</style>