<template>
    <div class="box"><slot></slot></div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name:'BoxInt',
    
})
</script>

<style scoped>
.box{
    background: #faf0ca;
}
</style>