<script setup>
import { ref } from 'vue';


const medidor = ref(0);
const max = 100;
const min = 0;
const mov = 10;


const incrementar  = () => {
console.log("incrementar");

    if (medidor.value < max){
     medidor.value += mov;
    
    }
}

const decrementar  = () => {
    console.log("decrementar");


    if (medidor.value > min){

     medidor.value -= mov;
    
    }
}
    



</script>

<template>


        <div class="ecualizador-columna">
            <button class="boton-control"  @click="incrementar">+</button>

        <div id="hueco">
            <div id="circulo" :style="{bottom: medidor + '%' }" ></div>
        </div>     
            <button class="boton-control" @click="decrementar">-</button>

            <input id="input_insercion"
                   type="number"
                   min="0"
                   max="100"
                   name="inserccion"/>

        </div>





</template>




<style scoped>

    .ecualizador-columna{
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 60px;
        background-color: rgb(197, 154, 193);
        border-color: black;

    }



    .boton-control{
        width: 22px;
        height: 22px;
        border-radius: 50%;
        background-color:  rgb(135, 134, 134);
        cursor: pointer;
        border: none;
        display: flex;
        align-items: center;
        justify-content: center;

    }


    
    #hueco{
        background-color: black;
        border-radius: 10px;
        margin: 10px 0;
        width: 3px;
        padding:5px ;
        height: 300px;
        position: relative;

    }

    #circulo{

        background-color: white;
        border-radius: 50%;
        width: 20px;
        height: 20px;
        margin: 0px -9px 0px -9px;        
        left: 50%;
        box-shadow: 0px 2px 1px 4px rgba(65, 63, 66, 0.5);
        position: absolute;
        cursor: pointer;
        bottom: 0%;
        transition: bottom 0.2s ease;
    }


    #input_insercion{
        width: 35px;
        text-align: center;
        margin-top: 10px;
        border-radius: 5px;
        border: 1px solid #ccc;
        display: block;


    }

</style>