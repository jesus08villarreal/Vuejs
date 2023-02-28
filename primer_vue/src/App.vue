<script setup>
import {ref, computed} from 'vue'

const positivo = ref(true);
const color = ref("color: green");
const counter = ref(0);
const ArrayFavoritos = ref([])
let checker1 = ref(false)
let indice
const checker2 = ref(false);
const checker3 = ref(false)


const showList = () => {
    if (ArrayFavoritos.value.length>0){
    checker2.value = true
    }else{
        checker3.value = true;
        console.log("Array vacio")
    }
}

const favNumber = () => { //array que guarda los numeros agregados a favorios y no deja agregar el mismo numero si ya se agrego una vez.
    const checker =ArrayFavoritos.value.indexOf(counter.value) //Solucionado con indexOf podemos saber si existe un valor dentro de una arreglo, si es que no existe entonces nos regresa -1
    if (checker!=-1){
        
        checker1.value=true                                  //Si si existe nos regresa como valor el indice o posicion de donde se encuentra este valor.
        console.log("Ese numero ya esta agregado")
    }else{
        
        ArrayFavoritos.value.push(counter.value)
        }
        checker2.value = false
    }

const increment = () => {
    checker1.value = false
    counter.value++

}
const decrement = () => {
    checker1.value = false
    counter.value--

}

const resetNumber = () => {
    checker1.value = false
    counter.value = 0;

}
const classCounter = computed(() => {
    if(counter.value>20){
        return 'bigger'
    }

    if(counter.value<0){
        return 'negative'
    }
    if(counter.value===0){
        return 'zero'
    }
    if(counter.value>0){
        return 'positive'
        
    }
})
</script>

<template>

    <h2 :class="classCounter">
        {{ counter }}
    </h2>
            
    <button @click="increment">Incrementar</button>
    <button @click="favNumber" :disabled="checker1">Agregar a favoritos</button>
    <button @click="decrement">Disminuir</button>
    <button @click="resetNumber">Resetear</button>
    <button @click="showList">Mostrar Lista</button>
    <p v-if="checker3">Lista de favoritos vacia.</p>
    <ul v-if="checker2===true">
        <li v-for="(numero,indice) in ArrayFavoritos" :key="numero">
        {{ ArrayFavoritos[indice] }}
        </li>
            </ul>
            <br>
    
    
</template>
<style>
.positive { 
    color: green;

}
.negative {
    color: blue;
}
.negative:hover {
    color: red;
    font-size: 1.6rem;
    transition: 3s
}
.zero {
    color: white;
    
}
.zero:hover {
    color: white;
    font-size: 3rem;
    transition: 2s;
}

.bigger {
    color: gold;
    font-size: 4rem;
}

</style>