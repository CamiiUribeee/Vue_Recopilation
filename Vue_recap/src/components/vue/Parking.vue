<script setup>

import {ref, computed} from 'vue'; 

const carBox = ref ([
    {active: true, value:2000},
    {active: true, value:2000},
    {active: true, value:2000},
    {active: true, value:2000},
    {active: true, value:2000},
    {active: true, value:2000}
])

const total = ref(0);

const toggleCarBox = (index) => {
const car = carBox.value[index]; 
car.active = !car.active; 
if (car.active){
    total.value += car.value; 

}

}


const bikeBox = ref([
    {active: true, value: 1000},
    {active: true, value: 1000},
    {active: true, value: 1000},
    {active: true, value: 1000},
    {active: true, value: 1000},
    {active: true, value: 1000},

])

const toggleBikeBox = (index) =>{
const bike = bikeBox.value[index]; 
bike.active = !bike.active;
if (bike.active){
    total.value += bike.value; 
}
}

const restarTotal = (computed) => {
    total.value -= total.value; 

}


const items = ["-hola", "-mundo"]
const ver = ref (false); 



</script>

<template>

    <div class="bg-slate-400">
        <h1 class="font-bold">Parqueadero</h1>
        <div class="flex flex-col" >
            <h2>Carros</h2>
            <div class="grid grid-cols-3 gap-2 mx-9">
                <div v-for="(car, index) in carBox" :key="index" >
                    <div @click="toggleCarBox(index)" :class="car.active ? 'bg-green-500 hover:bg-green-700' : 'bg-red-500 hover:bg-red-700'" class="w-20 h-20 flex items-center text-white cursor-pointer rounded-md justify-center">
                        {{ car.active ? 'Disponible' : 'Ocupado' }}
                    </div>
                </div>

            </div>
        </div>





        <div class="flex flex-col">
            <h2>Motos</h2>
            <div class="grid grid-cols-3 gap-2 mx-9">
                <div v-for="(bike, index) in bikeBox" :key="index">
                    <div @click="toggleBikeBox(index)" :class="bike.active ? 'bg-green-500 hover:bg-green-700' : 'bg-red-500 hover:bg-red-700'" class="h-20 w-20 flex justify-center items-center cursor-pointer rounded-md text-white">
                        {{ bike.active ? 'Disponible' : 'Ocupado' }}
                    </div>
                </div>
            </div>

        </div>



        <div>
            <h2>TOTAL</h2>
            <P>Total: {{ total }}</P>

        </div>

        <div>
            <button @click="restarTotal" class="cursor-pointer rounded-md border-black bg-cyan-300">Reiniciar el total</button>
        </div>




    </div>


    <div>
        <ul v-show="ver">
            <li v-for="item in items">
                {{ item }}

            </li>
        </ul>
        <button @click="ver=!ver">Click</button>
    </div>
   


</template>