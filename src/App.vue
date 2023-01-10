<script setup>
  import { ref, computed } from 'vue'
  import Header from './components/Header.vue'
  
  const cantidad = ref(10000);
  const MIN = 0;
  const MAX = 20000;
  const STEP = 100;

  const formatearDinero = computed(() => {
    const formatter = new Intl.NumberFormat('en-US', {
      style: 'currency',
      currency: 'USD'
    });

    return formatter.format(cantidad.value);
  });

  const handleChangeDecrement = () => {
    const VALOR = cantidad.value - STEP
    if( VALOR < MIN){
      alert('Cantidad no válida');
      return;
    }
    cantidad.value = VALOR
  }

  const handleChangeIncrement = () => {
    const VALOR = cantidad.value + STEP
    if( VALOR > MAX){
      alert('Cantidad no válida');
      return;
    }
    cantidad.value = VALOR
  }

</script>

<template>
  <div class="my-20 max-w-lg mx-auto bg-white shadow p-10">
    <Header />

    <div class="flex justify-between mt-10">
      <button
        class="h-10 w-10 flex items-center justify-center font-bold bg-lime-500 rounded-full hover:outline-none hover:ring-2 hover:ring-offset-2 hover:ring-lime-500 text-white text-2xl"
        @click="handleChangeDecrement"
      >-</button>
      <button
        class="h-10 w-10 flex items-center justify-center font-bold bg-lime-500 rounded-full hover:outline-none hover:ring-2 hover:ring-offset-2 hover:ring-lime-500 text-white text-2xl"
        @click="handleChangeIncrement"
      >+</button>
    </div>

    <div class="my-5">
      <input 
        type="range"
        class="w-full bg-gray-200 accent-lime-500 hover:accent-lime-600"
        :min="MIN"
        :max="MAX"
        :step="STEP"
        v-model.number="cantidad"
      />
      <!-- La opción más sencilla -->
      <p class="text-center my-10 text-5xl font-extrabold text-indigo-600">{{ formatearDinero }}</p>
      <!-- Otra opción, pero más rebuscada -->
      <!-- <p v-text="`$ ${cantidad}`"></p> -->
    </div>
  </div>
</template>
