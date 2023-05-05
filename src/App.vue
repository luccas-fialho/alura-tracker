<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <RegistroTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <BoxAtividade v-if="listaEstaVazia">
          Você não está muito produtivo hoje :(
        </BoxAtividade>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTarefa from './components/FormularioTarefa.vue';
import RegistroTarefa from './components/RegistroTarefa.vue';
import ITarefa from './interfaces/ITarefa'
import BoxAtividade from './components/BoxAtividade.vue';

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    FormularioTarefa,
    RegistroTarefa,
    BoxAtividade
  },
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.unshift(tarefa);
    }
  }
});
</script>

<style>
.lista {
  padding: 1.5rem;
}
</style>
