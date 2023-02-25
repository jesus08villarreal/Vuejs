<script setup>
var name = "Jesus Villarreal";
const ColorBlue = "color: blue";
const correcto = ["color: green", "CORRECTO", "respuesta correcta"];
const incorrecto = ["color: red", "INCORRECTO", "RESPUESTA INCORRECTA"];
const respuesta = true;

const arrayFrutas =[
    {
        name: "manzana",
        price: "3.00",
        description: "una manzana"
    },
    {
        name: "zanahoria",
        price: "2.00",
        description: "una manzana"
    },
    {
        name: "Espiruleta",
        price: "12.00",
        description: "una manzana"
    },
    {
        name: "cebolla",
        price: "23.00",
        description: "una manzana"
    },
    {
        name: "carne",
        price: "300.00",
        description: "una manzana"
    },
    
]

</script>

<template>
 
    <h3 :style="`${correcto[0]}`">{{name}} </h3>
    <h2 v-if="respuesta" :style="correcto[0]"> {{ correcto[1] }}</h2>
    <h2 v-if="!respuesta" :style="incorrecto[0]"> {{ incorrecto[1] }}</h2>
    <p v-if="!respuesta" :style="incorrecto[0]"> {{ incorrecto[2] }}</p>
    <p v-if="respuesta" :style="correcto[0]"> {{ correcto[2] }}</p>

    <ul>
       <li type="1" v-for="(fruta) in arrayFrutas" :key="fruta.name">
         -- {{ fruta.name }} -- {{ fruta.price }} -- {{ fruta.description }}
       </li> 
    </ul>

</template>
<style>
    h1 {
        color: red;
    }


</style>