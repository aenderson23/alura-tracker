<template>
    <button class="button" @click="clicked" :disabled="disable">
        <span class="icon">
            <i :class="icon"></i>
        </span>
        <span>{{texto}}</span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    props:{
        texto:{type:String,required:true},
        icon:{type:String,required:true},
        disable:{type:Boolean,default:false}
    },
    emits:['botaoClickado'],
    methods:{
        clicked(){
            this.$emit('botaoClickado')
        }
    }
})
</script>