<template>
  <h1 v-bind:style="miColor"> Hola, soy {{ miNombre }} y {{ mensaje }} </h1>
  <h2 v-bind:class="miClase">Hola, soy {{ miNombre }} y {{ mensaje }}</h2>
  <div class="text-center">
    <button class="btn btn-primary text-center" v-on:click="saludar">Saludar</button>
  </div>
  <br>
  <div class="text-center">
    <h4>Contador con variables reactivas</h4>
    <br>
    <div>
      <button @click="decremento" class="btn btn-danger">-</button>
      <span id="contador">{{ contador }}</span>
      <button @click="incremento" class="btn btn-success">+</button>
      <div v-show="comprobar">No está permitido el número 0</div>
    </div>
    <div>
      <h4>Array de datos externos(local)</h4>
      {{ unDato }}
    </div>
  </div>
</template>

<!-- ******************************************************************** -->

<script setup>
  import { ref, computed } from 'vue';
  const miNombre = "Pablo";
  const mensaje = "sigo vivo";
  const miColor = "color:green; font-size:3em";
  const miClase = "marron";

  const saludar = () => {
    console.log("Hola Pablo");
    alert("Hola Pablo");
  };
  const contador = ref(0);
  const decremento = () => {
    contador.value--;
  };
  const incremento = () => {
    contador.value++;
  };

  const comprobar = computed(() => {

    return contador.value === 0;
  });
  import { misDatos } from "./datos.js";
  const unDato = misDatos[2];
</script>

<!-- ********************************************************************** -->

<style lang="css" scoped>
  .marron {
    color: brown;
    font-size: 3em;
  }

  #contador {
    padding: 0 10px;
    font-size: xx-large
  }
</style>