<template>
    <header>
        <h1>
            <img src="../assets/alura.png" alt="" />
        </h1>
        <button type="button" class="botao" @click="alterarTema">
          {{ textoBotao }} 
        </button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data () {
      return {
        modoEscuroAtivo: false,
      }
    },
    computed:{
      textoBotao () {
        if (this.modoEscuroAtivo) { 
          return 'Desativar modo escuro'
      }
      else {
        return 'Ativar modo escuro'
      }
    }
    },
    methods: {
      alterarTema (){
        this.modoEscuroAtivo =!this.modoEscuroAtivo
        this.$emit('aoTemaAlterado',this.modoEscuroAtivo)
      }
    }
})
</script>

<style scoped>
/*aqui vai todo o estilo do componente */
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}

.botao { 
  background:linear-gradient(to bottom, #ededed 5%, #dfdfdf 100%);
	background-color:#ededed;
	border-radius:6px;
	border:1px solid #dcdcdc;
	display:inline-block;
	cursor:pointer;
	color:#2b2d42;
	font-family:Arial;
	font-size:17px;
	font-weight:bold;
	padding:9px 19px;
	text-decoration:none;
	text-shadow:0px 1px 0px #ffffff;
}
</style>