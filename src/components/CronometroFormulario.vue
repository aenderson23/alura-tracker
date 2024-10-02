<template>
    <section><strong class="display">{{tempoDecorrido}}</strong></section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name:"CronometroFormulario",
    props:{
        tempoEmSegundos:{type:Number,default:0, required:true}
    },
    computed:{
        tempoDecorrido():string{
            return new Date(this.tempoEmSegundos*1000).toISOString().substring(11,8+11)
        }
    },
})
</script>

<style>
.display{
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>