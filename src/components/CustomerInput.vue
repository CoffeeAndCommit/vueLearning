<template>
    
    <div class="input">
        <div class="fn text">
            <span>First Name</span>
        </div>
        <div class="firstName">
            <input type="text" id="firstname" placeholder="Enter First Name"  v-model="firstName">
        </div>
        <div class="ln text">
            <span>Last Name</span>
        </div>

        <div class="lastName">
            <label for="lastname"></label>
            <input type="text" id="lastname" placeholder="Enter Last Name" v-model="lastName" >
        </div>
        <div class="ad text">
            <span>Address</span>
        </div>
        <div class="address">
            <input type="text" id="address" placeholder="Enter Address" v-model="address">
        </div>
        
        <div class="add">
            <button @click="addData">Add</button>
   
        </div>
      
    </div>
</template>

<script setup>
import {ref} from 'vue';
import { defineEmits } from 'vue';

const emit = defineEmits(['addUser']);

let firstName = ref('');
let lastName = ref('');
let address = ref('');


let addData = ()=>{
    console.log("clicked");
    if(firstName.value.trim() !== '' && lastName.value.trim() !== '' && address.value.trim() !== ''){
        let  userData = {
        firstname: firstName.value,
        lastname: lastName.value,
        address: address.value,
        id: new Date().getTime(),
        };
        emit('addUser', userData);
        firstName.value ='';
        lastName.value ='';
        address.value ='';
    }else{
        alert('Fill The Value')
    }
  
      
   
}


</script>

<style scoped>
.text{
  font-weight: 500;
}

.input {
    width: 100vw; /* Full viewport width */
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    gap: 0.5rem;
    box-sizing: border-box; /* Prevents padding from exceeding width */
    padding: 1rem; /* Optional: for spacing */
  }
  input{
    width: 18vw;
  }
</style>