<template>
    <div class="details">
        <h1> Customer Details </h1>
        <div class="inputfields">
            <CustomerInput @addUser="addUserData"></CustomerInput>
           
            
        </div>
        <div class="cusDet">
             <CustomerDetail :items="items"  @removeUser="removeUserData"></CustomerDetail>
        </div>
    </div>
</template>

<script setup>
import CustomerInput from '@/components/CustomerInput.vue';
import CustomerDetail from '@/components/CustomerDetail.vue';
import {ref} from 'vue';

const items = ref([
  
]);

function addUserData(userData){
    items.value.push(userData);   
}
function removeUserData(id){
    items.value = items.value.filter(item => item.id !== id);
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