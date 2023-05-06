<template>
  <FormularioTarefa @aoSalvarTarefa="salvarTarefa" />
  <div class="lista">
    <RegistroTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
    <BoxAtividade v-if="listaEstaVazia">
      Você não está muito produtivo hoje :(
    </BoxAtividade>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import FormularioTarefa from '../components/FormularioTarefa.vue';
import RegistroTarefa from '../components/RegistroTarefa.vue';
import ITarefa from '../interfaces/ITarefa'
import BoxAtividade from '../components/BoxAtividade.vue';

export default defineComponent({
  name: "App",
  components: {
    FormularioTarefa,
    RegistroTarefa,
    BoxAtividade
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
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
