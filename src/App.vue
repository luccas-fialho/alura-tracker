<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-fifths">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-four-fifths conteudo">
      <!-- AQUI VAI A VIEW CORRESPONDENTE -->
      <Notificacoes />
      <router-view> </router-view>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Notificacoes from './components/Notificacoes.vue';

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    Notificacoes
  },
  data() {
    return {
      modoEscuroAtivo: false
    }
  },
  methods: {
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
.lista {
  padding: 1.5rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
  --bg-secundario: #faf0ca;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
  --bg-secundario: #13102c;
}

.conteudo {
  background-color: var(--bg-primario);
}</style>
