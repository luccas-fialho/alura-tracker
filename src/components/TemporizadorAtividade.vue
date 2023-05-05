<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroAtividade :tempoEmSegundos="tempoEmSegundos" />
    <BotaoAtividade @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando"/>
    <BotaoAtividade @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroAtividade from './CronometroAtividade.vue';
import BotaoAtividade from './BotaoAtividade.vue'

export default defineComponent({
  name: "TemporizadorAtividade",
  emits: ['aoTemporizadorFinalizado'],
  components: {
    CronometroAtividade,
    BotaoAtividade
  },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false
    };
  },
  methods: {
    iniciar() {
      // começar a contagem
      this.cronometroRodando = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
    },
    finalizar() {
      this.cronometroRodando = false;
      clearInterval(this.cronometro);
      // params: nome do evento a ser emitido, payload (quem tiver ouvindo o evento vai receber)
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos); // temporizador avisa que o evento foi emitido
      this.tempoEmSegundos = 0; // reseta o cronometro para a proxima tarefa
    }
  }
})
</script>

<style></style>