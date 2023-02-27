<script setup>
import {ref} from 'vue'

const increment = () => {
    
    counter.value++

}

const counter = ref(0);

</script>

<template>
 
    
       <template type="1"  v-for="(fruta) in arrayFrutas" :key="fruta.name">
        <li v-if="fruta.price>0">
         -- {{ fruta.name }} -- {{ fruta.price }} -- {{ fruta.description }}
        </li>
           </template> 
            
    <button @click="increment">Hol!</button>
    <h2>{{ counter }}</h2>

</template>
<style>
    h1 {
        color: red;
    }


</style>