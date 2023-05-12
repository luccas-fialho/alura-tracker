<template>
  <div class="box has-text-weight-bold">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'BoxAtividade'
})
</script>

<style scoped>
.box {
  background: var(--bg-secundario);
  color: var(--texto-primario);
}
</style>