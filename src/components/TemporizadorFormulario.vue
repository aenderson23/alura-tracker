<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroFormulario :tempoEmSegundos="tempoEmSegundos" />
        <BotaoTemporizador texto="play" icon="fas fa-play" @botao-clickado="iniciar" :disable="cronometroRodando"/>
        <BotaoTemporizador texto="stop" icon="fas fa-stop" @botao-clickado="finalizar" :disable="!cronometroRodando"/>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroFormulario from './CronometroFormulario.vue';
import BotaoTemporizador from './BotaoTemporizador.vue';

export default defineComponent({
    name: "TemporizadorRomulario",
    emits:['aoTemporizadorFinalizado'],
    data(){
        return{
            tempoEmSegundos:0,
            cronometro: 0,
            cronometroRodando:false
        }
    },
    components:{CronometroFormulario,BotaoTemporizador},
    methods:{
        iniciar(){
            this.cronometroRodando=true
            this.cronometro=setInterval(()=>{this.tempoEmSegundos++},1000)
            console.log('iniciando')
        },
        finalizar(){
            this.cronometroRodando=false
            clearInterval(this.cronometro)
            console.log('finalizando')
            this.$emit('aoTemporizadorFinalizado',this.tempoEmSegundos)
            this.tempoEmSegundos=0
        }
    }
})
</script>