<template>
  <header>
    <h1>
      <img src="https://api.lorem.space/image" alt="img">
    </h1>
    <button class="button" @click="alterarTema"> {{ textoBotao }}</button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: "BarraLateral",
  emits:['aoTemaAlterado'],
  data(){
    return{
      modoEscuroAtivo: false
    }
  },
  computed: {
    textoBotao(){
      if (this.modoEscuroAtivo) {
        return 'Desativar Dark Mode'
      }
      return 'Ativar Dark Mode'
    }
  },
  methods:{
    alterarTema(){
      this.modoEscuroAtivo = !this.modoEscuroAtivo
      this.$emit('aoTemaAlterado',this.modoEscuroAtivo)

    }
  }
});
</script>

<style scoped>
</style>