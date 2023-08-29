<template>
  <main class="apresentacao" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="apresentacao__barraLateral">
      <BarraLateral @aoTemaAlterado="trocarTema"></BarraLateral>
    </div>
    <div class="conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefas"></Formulario>
      <div class="lista">
        <TarefaComponent v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" ></TarefaComponent>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Formulario from './components/Formulario.vue';
import TarefaComponent from './components/Tarefa.vue';
import ITarefas from './interfaces/ITarefa'
export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    TarefaComponent
  },
  data() {
    return {
      tarefas: [] as ITarefas[],
      modoEscuroAtivo:false
    }
  },
  methods: {
    salvarTarefas(tarefa: ITarefas) {
      this.tarefas.push(tarefa)
    },
    trocarTema (modoEscuroAtivo : boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main{
  --bg-primario: #fff;
  --texto-primario: #000;
  
}
main.modo-escuro{
  --bg-primario: #161616;
  --texto-primario: #a30b0b;
}
.conteudo {
  background-color: var(--bg-primario);
}

.apresentacao{
  margin: 2% 20% 2% 20%;
}
.apresentacao__barraLateral{
display: flex;
justify-content: center;
padding-bottom: 5%;
}



</style>
