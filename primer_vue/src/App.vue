<script setup>
import {ref, computed} from 'vue'

const positivo = ref(true);
const color = ref("color: green");
const counter = ref(0);
const ArrayFavoritos = []
const buleano = ref(false)
let indice


const showList = () => {
    for(indice in ArrayFavoritos) {
        console.log(ArrayFavoritos[indice])
     }
}

const favNumber = () => { //array que guarda los numeros agregados a favorios y no deja agregar el mismo numero si ya se agrego una vez.
    let checker = counter.value
    if (counter.value==ArrayFavoritos.includes(checker)){ //atorado aqui para revisar si ya se puso 1 vez el numero favorito
        console.log("Ese numero ya esta agregado")
    }else{
        ArrayFavoritos.push(counter.value)
        }
}

const increment = () => {
    
    counter.value++

}
const decrement = () => {
    
    counter.value--

}

const resetNumber = () => {
    
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
    <button @click="favNumber">Agregar a favoritos</button>
    <button @click="decrement">Disminuir</button>
    <button @click="resetNumber">Resetear</button>
    <button @click="showList">Mostrar Lista</button>
    
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