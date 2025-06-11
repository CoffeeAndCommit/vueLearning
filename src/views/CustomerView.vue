<template>
    <div class="details">
        <h1> Customer Details </h1>
        <div class="inputfields">
            <CustomerInput @addUser="addUserData"></CustomerInput>
           
            
        </div>
        <div class="cusDet">
             <CustomerDetail :items="items"  @removeUser="removeUserData" @editUser="editUser"></CustomerDetail>
        </div>
        <div class="edit" v-if="showedit">
            <CustomerEdit :item="editData" @closeModal="showedit=false" @editUser="editUserValue" ></CustomerEdit>
        </div>
    </div>
</template>

<script setup>
import CustomerInput from '@/components/CustomerInput.vue';
import CustomerDetail from '@/components/CustomerDetail.vue';
import CustomerEdit from '@/components/CustomerEdit.vue';

import {ref} from 'vue';

const items = ref([
  
]);

const editData = ref({});

const showedit = ref(false);


function addUserData(userData){

    items.value.push(userData);   
}
function removeUserData(id){
    items.value = items.value.filter(item => item.id !== id);
}
function editUser(id){
    showedit.value = true;
    editData.value = items.value.find(item => item.id === id);
    
    }
function editUserValue(editedValue){
        showedit.value = false;
        const index = items.value.findIndex(item => item.id === editedValue.id);
        if (index !== -1) {
            items.value.splice(index, 1, { ...editedValue });
        }
        
    }

</script>

<style scoped>

.details {
    display: flex;
    flex-direction: column;
    align-items: flex-start;   
    padding-left: 4rem;
    padding-right: 4rem
  }
  
</style>