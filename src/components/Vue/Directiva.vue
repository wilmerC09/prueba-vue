<template>
  <div class="border-2 shadow mx-auto py-6 px-5  mt-10 ">
    <h1 class="uppercase text-center font-semibold">restaurante ufpso</h1>
    <div class="flex space-x-4 px-2 py-2 ">
      <div class=" mt-4 px-2 py-1 items-center">
      <ul>
        <li @click=" mostrarMenu('lunes')">Lunes </li>
        <li @click="mostrarMenu('martes')">martes </li>
        <li>miercoles </li>
        <li>jueves </li>
        <li>viernes</li>
        <li>sabado </li>
      </ul>
    </div>
    <div v-if="diaActual" class="flex flex-col space-y-4 px-2 py-1">
        <button @click="mostrarDesayuno = true; mostrarAlmuerzo = false; mostrarCena = false;" class="bg-blue-500 text-white px-3 py-2 rounded">Desayuno</button>
        <button @click="mostrarDesayuno = false; mostrarAlmuerzo = true; mostrarCena = false;" class="bg-green-500 text-white px-3 py-2 rounded">Almuerzo</button>
        <button @click="mostrarDesayuno = false; mostrarAlmuerzo = false; mostrarCena = true;" class="bg-red-500 text-white px-3 py-2 rounded">Cena</button>

        <div v-if="mostrarDesayuno">
          <h1>DESAYUNO</h1>
          <ul>
            <li v-for="(desayunoItem, index) in menu[diaActual].desayuno" :key="index">
              {{ desayunoItem.mañana }} - {{ desayunoItem.tarde }} - {{ desayunoItem.noche }}
            </li>
          </ul>
        </div>

      <ol>
        <h1>ALMUERZO</h1>
        <li v-for="(almuerzos,index) in almuerzo">
         {{ almuerzos.mañana }}
         {{  almuerzos.tarde }}
         {{ almuerzos.noche }}
        </li>
      </ol>
      <ol>
        <h1>ALMUERZO</h1>
        <li v-for="( cenas,index) in cena">
         {{ cenas.mañana }}
         {{  cenas.tarde }}
         {{ cenas.noche }}
        </li>
      </ol>
      
     
    </div>
    </div>
  

  </div>
</template>

<script setup>
import { ref } from 'vue';

const diaAactual = ref(null)


const menu = ref({
  lunes: {
    desayuno: [
      { mañana: "arepa", tarde: "empanada", noche: "sopa" }
    ],
    almuerzo: [
      { mañana: "frutas", tarde: "arroz", noche: "pollo" }
    ],
    cena: [
      { mañana: "pan", tarde: "queso", noche: "carne" }
    ]
  },
  martes: {
    desayuno: [
      { mañana: "pancakes", tarde: "sandwich", noche: "ensalada" }
    ],
    almuerzo: [
      { mañana: "batido", tarde: "pasta", noche: "pescado" }
    ],
    cena: [
      { mañana: "yogurt", tarde: "sopa", noche: "tacos" }
    ]
  },
  miercoles: {
    desayuno: [
      { mañana: "huevos", tarde: "pollo", noche: "pasta" }
    ],
    almuerzo: [
      { mañana: "jugo", tarde: "ensalada", noche: "carne" }
    ],
    cena: [
      { mañana: "frutas", tarde: "pizza", noche: "sushi" }
    ]
  },
  jueves: {
    desayuno: [
      { mañana: "cereal", tarde: "pizza", noche: "sushi" }
    ],
    almuerzo: [
      { mañana: "batido", tarde: "ensalada", noche: "hamburguesa" }
    ],
    cena: [
      { mañana: "frutas", tarde: "arroz", noche: "pasta" }
    ]
  },
  viernes: {
    desayuno: [
      { mañana: "frutas", tarde: "hamburguesa", noche: "tacos" }
    ],
    almuerzo: [
      { mañana: "yogurt", tarde: "sandwich", noche: "sopa" }
    ],
    cena: [
      { mañana: "pan", tarde: "queso", noche: "pollo" }
    ]
  },
  sabado: {
    desayuno: [
      { mañana: "pan", tarde: "queso", noche: "carne" }
    ],
    almuerzo: [
      { mañana: "batido", tarde: "ensalada", noche: "pasta" }
    ],
    cena: [
      { mañana: "jugo", tarde: "arroz", noche: "pescado" }
    ]
  }
});

const mostrarMenu = (dia) => {
  diaActual.value = dia;
};
</script>



