<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro':modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioInicial @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefaMain v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxInt v-if="tarefas.length==0">
          Voce não está muito produtivo hoje
        </BoxInt>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioInicial from './components/FormularioInicial.vue'
import TarefaMain from './components/TarefaMain.vue';
import ITarefa from './interfaces/ITarefa';
import BoxInt from './components/BoxInt.vue';
export default defineComponent({
  name: 'App',
  components:{BarraLateral,FormularioInicial,TarefaMain,BoxInt},
  data() {
    return {
      tarefas:[] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  methods:{
    salvarTarefa(tarefa:ITarefa):void{
      this.tarefas.push(tarefa)
    },
    trocarTema(modoEscuroAtivo:boolean){
      this.modoEscuroAtivo=modoEscuroAtivo
    }
  }
});
</script>

<style>
.lista{
  padding: 1.25rem;
}
main{
  --bg-primario:#fff;
  --texto-primario:#000;
}
main.modo-escuro{
  --bg-primario:#2b2b42;
  --texto-primario:#ddd;
}

.conteudo{
  background-color: var(--bg-primario);
}
</style>
