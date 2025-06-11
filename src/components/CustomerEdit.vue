<script setup>
import { reactive , defineEmits,} from 'vue';
import { defineProps } from 'vue';

const prop = defineProps({
    item: {
    type: Object,
    required: true,
  },
});

// Create a reactive copy of the item to edit
const editedValue = reactive({
  firstname: prop.item.firstname,
  lastname: prop.item.lastname,
  address: prop.item.address,
  email: prop.item.email,
  id: prop.item.id,
});
const emit = defineEmits(['editUser' , 'closeModal']);

const editValue = ()=>{
    emit('editUser',editedValue);
}
const closeModal =()=>{
    emit('closeModal' , false);

    
}
console.log(editedValue);



</script>

<template>
 <div>  

    <div class="overlay" id="editModal">
        <div class="modal">
       
          <h2>Edit User Details</h2>
          <label for="firstName">First Name</label>
          <input type="text" id="firstName" placeholder="Enter First Name" v-model="editedValue.firstname">
    
          <label for="lastName">Last Name</label>
          <input type="text" id="lastName" placeholder="Enter Last Name"  v-model="editedValue.lastname">
 
    
          <label for="address">Address</label>
          <input type="text" id="address" placeholder="Enter Address" v-model="editedValue.address">
    
          <label for="email">Email</label>
          <input type="email" id="email" placeholder="Enter Email"  v-model="editedValue.email">
    
          <div class="actions">
            <button class="save" @click="editValue()">Save</button>
            <button class="cancel"  @click="closeModal()">Cancel</button>
          </div>
        </div>
      </div>
    
 </div>
</template>
<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  background-color: #f2f2f2;
}

.overlay {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.6);

  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal {
  background: #fff;
  padding: 30px;
  border-radius: 12px;
  width: 400px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
  position: relative;
  margin: auto;
  margin-top: 100px;
}

.modal h2 {
  margin-top: 0;
  margin-bottom: 20px;
  font-size: 24px;
  color: #333;
}

.modal .close {
  position: absolute;
  right: 15px;
  top: 10px;
  font-size: 24px;
  cursor: pointer;
  color: #aaa;
}

.modal .close:hover {
  color: #333;
}

.modal label {
  display: block;
  margin-top: 10px;
  font-weight: bold;
  font-size: 14px;
}

.modal input[type="text"],
.modal input[type="email"] {
  width: 100%;
  padding: 10px;
  margin-top: 5px;
  border: 1px solid #ccc;
  border-radius: 6px;
}

.modal .actions {
  margin-top: 20px;
  display: flex;
  justify-content: flex-end;
  gap: 10px;
}

.modal .actions button {
  padding: 10px 18px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
}

.modal .actions .save {
  background-color: #4CAF50;
  color: white;
}

.modal .actions .cancel {
  background-color: #ccc;
}
</style>