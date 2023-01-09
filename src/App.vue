<script setup>
  import { ref } from 'vue'
  import Header from './components/Header.vue'
  
  const cantidad = ref(10000);
  const MIN = 0;
  const MAX = 20000;
  const STEP = 100;

  function handleChange(e){
    cantidad.value = +e.target.value;
  }

</script>

<template>
  <div class="my-20 max-w-lg mx-auto bg-white shadow p-10">
    <Header />

    <div class="my-5">
      <input 
        type="range"
        class="w-full bg-gray-200 accent-lime-500 hover:accent-lime-600"
        min="0"
        max="20000"
        step="100"
        value="10000"
        @input="handleChange"
      />
      <!-- La opción más sencilla -->
      <p>$ {{ cantidad }}</p>
      <!-- Otra opción, pero más rebuscada -->
      <!-- <p v-text="`$ ${cantidad}`"></p> -->
    </div>
  </div>
</template>
