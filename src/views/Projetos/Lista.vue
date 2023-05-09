<template>
  <section class="botao-novo">
    <router-link to="/projetos/novo" class="button is-warning">
      <span class="icon is-small">
        <i class="fas fa-plus"></i>
      </span>
      <span>Novo projeto</span>
    </router-link>
    <table class="table is-fullwidth tabela">
      <thead class="thead">
        <tr>
          <th>ID</th>
          <th>Nome</th>
          <th>Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="projeto in projetos" :key="projeto.id">
          <td>{{ projeto.id }}</td>
          <td>{{ projeto.nome }}</td>
          <td>
            <router-link :to="`/projetos/${projeto.id}`" class="button is-warning">
              <span class="icon is-small">
                <i class="fas fa-pencil-alt"></i>
              </span>
            </router-link>
            <button class="button ml-2 is-danger" @click="excluir(projeto.id)">
              <span class="icon is-small">
                <i class="fas fa-trash"></i>
              </span>
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </section>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
import { useStore } from '@/store'
import { EXCLUIR_PROJETO } from '@/store/tipo-mutacoes';

export default defineComponent({
  name: 'ListaTarefa',
  methods: {
    excluir(id: string) {
      this.store.commit(EXCLUIR_PROJETO, id)
    }
  },
  setup() {
    const store = useStore()
    return {
      projetos: computed(() => store.state.projetos),
      store
    }
  }
})
</script>

<style>
.botao-novo {
  background-color: var(--bg-primario);
}
.tabela {
  background-color: var(--bg-primario);
  color: var(--texto-primario)
}
.thead tr th {
  color: var(--texto-primario);
}
</style>
