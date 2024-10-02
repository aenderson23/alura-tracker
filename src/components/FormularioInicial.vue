<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
                <TemporizadorFormulario @ao-temporizador-finalizado="finalizarTarefa"/>
            </div>
        </div>

    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorFormulario from './TemporizadorFormulario.vue';

export default defineComponent({
    name: "FormularioInicial",
    components:{TemporizadorFormulario},
    methods:{
        finalizarTarefa(tempoEmSegundos:number):void{
            this.$emit('aoSalvarTarefa',{
                descricao:this.descricao,
                duracaoEmSegundos:tempoEmSegundos
            })
            this.descricao=''
        }
    },
    data(){
        return {
            descricao:''
        }
    },
    emits:['aoSalvarTarefa']
})
</script>

<style>
.formulario{
    color:var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>