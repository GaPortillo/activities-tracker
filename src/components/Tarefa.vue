<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column">Descricao da tarefa</div>
      <div class="column">
        <Cronometro :tempoEmSegundos="15"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  name: "TarefaComponent",
  components: {
    Cronometro,
  },
});
</script>

<style scoped>
.box {
    background: #FAF0CA;
}
</style>
