<template>
  <div class="box formulario">
    <div class="columns">
      <div class="column is-9" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input type="text" class="input" placeholder="Qual a tarefa você deseja iniciar?" v-model="descricao">
      </div>
      <div class="column">
        <TemporizadorAtividade @aoTemporizadorFinalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorAtividade from './TemporizadorAtividade.vue';

export default defineComponent({
  name: "FormularioTarefa",
  emits: ['aoSalvarTarefa'],
  components: {
    TemporizadorAtividade
  },
  data() { // método que retorna o estado
    return {
      descricao: ''
    }
  },
  methods: {
    finalizarTarefa(tempoDecorrido: number): void {
      this.$emit('aoSalvarTarefa', {
        duracaoEmSegundos: tempoDecorrido,
        descricao: this.descricao
      })
      this.descricao = '';
    }
  }
})
</script>

<style>
.formulario {
  color: var(--texto-primario);
  background-color: var(--bg-primario);
}
</style>