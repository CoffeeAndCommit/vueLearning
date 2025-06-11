<script setup>
import {defineProps} from 'vue';
import { defineEmits } from 'vue';

const emit = defineEmits(['removeUser']);

const props = defineProps({
        items: {
          type: Array,
          required: true,
        },
     });

let removeData =(id)=>{
    emit('removeUser', id);
}

</script>

<template>
 <div>  
  <table>
    <tr v-for="item in props.items" :key="item.id">
      <td>{{ item.firstname }}</td>
      <td>{{ item.lastname }}</td>
      <td>{{ item.address }}</td>
      <td><button v-on:click="removeData(item.id)">X</button>
        <button @click="h">🖊️</button>
      </td>
    </tr>
  </table>
 
</div>
</template>

<style scoped>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
  margin: 1rem;
 
}
td {
  border: 1px solid black; 
  padding-left: 4px;
  text-align: left;     
  font-weight: 500;   
}
td:nth-child(1), td:nth-child(2), td:nth-child(3){
  width: 22vw;
}
td:nth-child(4){
  width: 10vw;
}


table tr:nth-child(1), table tr:nth-child(3) {
  background-color: #FFE83A;
}
table tr{
  background-color: #D8CD8D;
}
button{
margin-right: 10px;
}
</style>