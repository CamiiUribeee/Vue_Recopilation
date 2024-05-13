<script setup>

import {ref} from 'vue';
const counter = ref(0); 


function decrement(){
    if (counter.value>0 ){
        counter.value--;
    }

}

function increment(){
    counter.value++; 
}

</script>




<template>
    <div class="bg-purple-400 rounded flex-col flex items-center py-8 px-6 w-96" >
        <div class="relative">  <!-- ese size es como el tamaño general de todo el div -->
            <img class="rounded-full size-36" 
            src="https://wi.wallpapertip.com/wsimgs/5-50066_flash-1280-x-flash-wallpaper-ipod.jpg" alt="">

            <!-- Este div es para el circulito rojo (notificación) -->
            <div v-show="counter>0" class="rounded-full bg-red-600 absolute top-0 right-0 size-7 flex justify-center items-center"  >
                <!-- el top es para acomodar el circulito en la parte superior, en la parte superior del div padre (sin importar la posicion inicial de ese circulito) -->
                {{ counter }}
            </div>
            <p v-if="counter >0">Nuevos mensajitos!!!!!</p>
            <p v-else>No hay mensajes</p>

        </div>

        <div class="flex justify-around w-24 mt-6">
            <!-- el w-24 es para el ancho y el mt-6 es para espaciado verticalmente hablando -->
            <!-- el justify around es para que todo quede horizontal en vez de vertical -->
            <button @click="decrement" class="bg-purple-800 text-white rounded flex justify-center items-center px-2 w-6 ">
                <!-- w para el ancho de la cajita -->
                -
            </button>
            {{ counter }}

            <button @click="increment" class="bg-purple-800 text-white rounded flex justify-center items-center px-2 w-6" >
                +
            </button>

        </div>


        
        
    </div>
    

</template>