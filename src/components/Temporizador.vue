<template>
    <section class="is-flex is-align-items-center is-justify-content-space-between">
      <Cronometro :tempoEmSegundos="tempoEmSegundos"/>
      <Button @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando"/>
      <Button @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando"/>
    </section>
  </template>
  <script lang="ts">
  import { defineComponent } from "vue";
  import Cronometro from "./Cronometro.vue";
  import Button from "./Button.vue";
  
  export default defineComponent({
      name: "TemporizadorComponent",
      emits: ['aoTemporizadorFinalizado'],
      components: {
          Cronometro,
          Button,
      },
      data() {
          return {
              tempoEmSegundos: 0,
              cronometro: 0,
              cronometroRodando: false,
          };
      },
      methods: {
          iniciar() {
              // Iniciar contagem
              this.cronometroRodando = true;
              this.cronometro = setInterval(() => {
                  this.tempoEmSegundos += 1;
              }, 1000);
          },
          finalizar() {
              // Finalizar contagem
              this.cronometroRodando = false;
              clearInterval(this.cronometro);
              this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
              this.tempoEmSegundos = 0;
          },
      },
  });
  </script>
  