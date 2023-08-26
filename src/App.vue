<template>
  <main class= "columns is-gapless is-multiline">
    <div class="colum is-one-quarter">
      <BarraLateral></BarraLateral>
    </div>
    <div class="colum is-three-quarter">
      <Formulario></Formulario>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Formulario from './components/Formulario.vue';
export default defineComponent({
  name: 'App',
  components:{
    BarraLateral,
    Formulario
    
  }
});
</script>

<style>


</style>
