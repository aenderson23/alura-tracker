<template>
    <BoxInt>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <CronometroFormulario :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxInt>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroFormulario from './CronometroFormulario.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxInt from './BoxInt.vue';
export default defineComponent({
    name:'TarefaMain',
    components:{CronometroFormulario,BoxInt},
    props:{
        tarefa:{
            type: Object as PropType<ITarefa>, required:true
        }
    }
})
</script>

<style scoped>
.box{
    background: #faf0ca;
}
</style>