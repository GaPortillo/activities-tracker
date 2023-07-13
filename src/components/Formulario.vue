<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulario para criacao de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa voce deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Temporizador from "./Temporizador.vue";

export default defineComponent({
    name: "FormularioComponent",
    components: {
        Temporizador
    },
    data () {
      return {
        descricao: ""
      }
    },
    methods: {
        finalizarTarefa (tempoDecorrido: number) : void {
            console.log('tempo da tarefa',tempoDecorrido)
            console.log('descricao da tarefa:',this.descricao)
            this.descricao = ''

        }
    },
});
</script>
