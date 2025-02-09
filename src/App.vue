<script setup>
import { ref } from 'vue';

const name = ref('Jean');
const status = ref('Active');
const nation = ref('Mondstadt');
const vision = ref('Anemo');
const race = ref('Human');
const others = ref(['Tall Girl', 'Leo Minor', 'Invigorating Pizza']);

// Create a ref to store the new detail input
const newDetail = ref('');

// Toggle the status between 'Active' and 'Inactive'
const toggleGetJean = () => {
  if (status.value === 'Active') {
    status.value = 'Inactive';
  } else if (status.value === 'Inactive') {
    status.value = 'Active';
  }
};

// Add new detail to the list
const addDetails = () => {
  if (newDetail.value.trim() !== '') {
    others.value.push(newDetail.value);
    newDetail.value = '';  // Clear the input after adding
  }
};

const delDetails = (index) =>{
  others.value.splice(index, 1);
};
</script>

<template>
  <h1>Genshin Daily</h1>
  <h1> Name: {{ name }}</h1>
  <h1> Status: {{ status }}</h1>

  <h3>Supports:</h3>
  <ul>
    <li v-for="(traits, index) in others" :key="index">
      <span>
        {{ traits }}
      </span>
      <button @click="delDetails(index)">x</button>
    </li>
  </ul>
  
  <div>
    <button @click="toggleGetJean">Click to include Jean</button>
  </div>

  <form @submit.prevent="addDetails">
    <label for="newDetails">Add more</label><br>
    <!-- Bind the input to the 'newDetail' ref using v-model -->
    <input type="text" id="newDetails" v-model="newDetail"><br>
    <button type="submit">Add</button>
  </form>
</template>
