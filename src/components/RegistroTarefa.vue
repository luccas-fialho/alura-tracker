<template>
  <BoxAtividade>
    <div class="columns">
      <div class="column is-4">{{ tarefa.descricao || 'Tarefa sem descrição' }}</div>
      <div class="column is-3">
        {{ tarefa.projeto?.nome || 'N/D' }}
      </div>
      <div class="column">
        <CronometroAtividade :tempoEmSegundos="tarefa.duracaoEmSegundos" />
      </div>
    </div>
  </BoxAtividade>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroAtividade from './CronometroAtividade.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxAtividade from './BoxAtividade.vue';

export default defineComponent({
  name: 'RegistroTarefa',
  components: {
    CronometroAtividade,
    BoxAtividade
  },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true
    }
  }
})
</script>
