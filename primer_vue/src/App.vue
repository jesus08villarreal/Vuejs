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
    <div class="container text-center row">

        
        <h2 :class="classCounter" class="text-center">
            {{ counter }}
        </h2>
        
        <div class="btn-group-vertical col-sm">
        <button @click="increment" class="btn btn-success">Incrementar</button>
        <button @click="decrement" class="btn btn-danger">Disminuir</button>
        <button @click="favNumber" :disabled="checker1" class="btn btn-primary">Agregar a favoritos</button>
        <button @click="resetNumber" class="btn btn-light">Resetear</button>
        <button @click="showList" class="btn btn-info">Mostrar Lista</button>
        <p v-if="checker3" class="btn btn-secondary">Lista de favoritos vacia.</p> 
            </div>
            <div class="container col">
        
        <ul v-if="checker2===true" class="list-group">
            <li v-for="(numero,indice) in ArrayFavoritos" :key="numero" class="list-group-item"> 
                {{ ArrayFavoritos[indice] }}
            </li>
        </ul>
        </div>
    </div>
        
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