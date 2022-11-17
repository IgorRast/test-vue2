<template>
  <div>
  <v-row class="row">
    <v-text-field @keyup.enter="addLSPrice" class="form1" :rules="rules" id="f1" v-model="age"></v-text-field>
    
    <v-text-field @keyup.enter="addLSQty" class="form1" :rules="rules" id="f2" v-model="value"></v-text-field>
    <v-text-field @keyup.enter="addLSAm" class="form1" :rules="rules" id="f3" v-model="value"></v-text-field>
   
    <v-btn @click="recount()" class="btn-1" depressed bottom>
    Button
    </v-btn>
  </v-row>
  <v-row>
    <p>{{age}}</p>
    <p>1212</p>
    <p>1212</p>
  </v-row>
  <div id="output" >
    <p>Value</p>
  </div>
  <v-card
  elevation="10"
  height="200px"
  outlined
><p class="msg">Message</p></v-card>
</div>
</template>

<script>


  export default {
    name: 'TableTask',

    data () {
    return {
      
      age: 0,
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
      let name = document.getElementById('f2').value
      localStorage.setItem('Quantity', name )
      document.getElementById('f2').value = '' 
      
         
       
        },
        addLSAm() {
      let name = document.getElementById('f3').value
      let message = document.querySelector('.msg')
      if (name % 2 === 0) {
      localStorage.setItem('Amount', name )
      message.textContent = 'message-true'  
      }
      else {
        message.textContent = 'message-false'   
      }
      document.getElementById('f3').value = '' 
         
       
        },
    showLS() {
      let output = document.getElementById("output")
      for (let i = 0; i < localStorage.length; i++) {
    let element = document.createElement("p")
    
    element.textContent = localStorage.getItem(localStorage.key(i))
    output.appendChild(element)
}
    },
    recount() {
      let index = localStorage.getItem('operationIndex')
      localStorage.setItem('operationIndex', +index + 1)
      console.log(localStorage.getItem('operationIndex'))
    }    
        
      },
   mounted() {
    localStorage.setItem('operationIndex', 0)
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