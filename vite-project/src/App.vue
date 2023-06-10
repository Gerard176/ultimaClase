<script setup>
import { ref,computed } from 'vue';
const valorBoleta = 5000
let cantidadEntradas = ref(false)
const mostrarMensaje = computed(()=>{
  return cantidadEntradas.value >= 4 ? true : false
})
const comprarBoletas = () =>{
  const cant = parseInt(cantidadEntradas)
  if (cant>= 4) {
    const valorPleno = cant * valorBoleta
    const descuento = valorPleno*.3  
    valorTotal.value = valorPleno - descuento
  }else{
    valorTotal.value = cant*valorBoleta
  }
  
  
  
}
const valorTotal = ref(0)
</script>

<template>
  <div class="bg-slate-200 w-96 mx-auto py-4 px-6 rounded-md mt-8 shadow-md flex justify-center">
    <label class="px-2" for="entradas">
      Cantidad
    </label>
    <input class="border-black border-2 rounded-md" id="entradas" name="entradas" v-model="cantidadEntradas" type="text">
    <button @click="comprarBoletas()" class="ml-2 bg-blue-300 px-2 rounded-md">
      Comprar
    </button>
    
    
  </div>
  <div class="mx-auto w-96">
      <p>
      Valor total : {{ valorTotal}}
      </p>
      <span class="text-red-700 font-extrabold" v-if="mostrarMensaje">
        Descuento de lo mio
      </span>
  </div>
  
</template>

<style scoped>

</style>
