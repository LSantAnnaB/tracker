<template>
  <main class="columns is-gapless is-multiline modo-escuro">
    <div class="colum is-one-quarter">
      <BarraLateral></BarraLateral>
    </div>
    <div class="colum is-three-quarter conteudo">
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
      tarefas: [] as ITarefas[]
    }
  },
  methods: {
    salvarTarefas(tarefa: ITarefas) {
      this.tarefas.push(tarefa)
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
main{
  --bg-primario: #202d42;
  --texto-primario: #ddd;
}
.conteudo {
  background-color: var(--bg-primario);
}

</style>
