<template>
  <div class="formulario" >
    <div class="columns">
      <div class="columns__texto" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input 
          class="input" 
          type="text" 
          placeholder="Qual tarefa você deseja iniciar?" 
          v-model="descricao" />
      </div>
      <div class="column">
        <Temporizador @ao-temporizador-finalizado="finalizarTarefa"></Temporizador>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Temporizador from "./Temporizador.vue";
export default defineComponent({
  name: "FormulárioComponent",
  emits:['aoSalvarTarefa'],
  components: {
    Temporizador
  },
  data(){
    return{
      descricao:``
  }
  },
  methods: {
    finalizarTarefa(tempoDecorrido: number): void {
      this.$emit('aoSalvarTarefa',{
        duracaoEmSegundos: tempoDecorrido,
        descricao: this.descricao
      })
      this.descricao = ''
    }
  }
});
</script>

<style scoped>
.formulario{
  color: var(--texto-primario);
  background-color: var(--bg-primario);
}
.columns{
  margin-left: 8%;
  margin-right: 8%;
  padding: 2%;
  display: flex;
  flex-direction: column;
  
}

.columns__texto{
 margin-left: 10%; 
 width: 80%;
 align-items: center;
}
.input{
  text-align: center;

}
</style>