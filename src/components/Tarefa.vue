<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">
        {{ tarefa.descricao || "Tarefa sem descrição"}}
      </div>
      <div class="column">
        <Cronometro :tempo-em-segundos="tarefa.duracaoEmSegundos"></Cronometro>
      </div>
    </div>
  </div>
</template>

<script lang="ts">

import { defineComponent, PropType } from 'vue';
import Cronometro from './Cronometro.vue';
import ITarefa from '@/interfaces/ITarefa';

export default defineComponent({
  name: 'TarefaComponent',
  components: {
    Cronometro,
  },
  props: {
    tarefa:{
      type: Object as PropType<ITarefa>,
        required:true
    }
  }
});

</script>

<style scoped>

.box{
  background: rgb(187, 246, 155);
}
 
</style>