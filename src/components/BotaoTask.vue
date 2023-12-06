<template>
    <button class="button" @click="clicado" :disabled="desabilitado">
      <span class="icon">
        <i :class="icone"></i>
      </span>
      <span>{{ texto }}</span>
    </button>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BottaoTask',
    emits: ['clicado'],
    props: {
        desabilitado: {
            type:Boolean
        },
        icone: {
            type: String,
            default: 'iniciar'
        },
        texto: {
            type: String,
            default: 'iniciar'
        }
    },
    methods: {
        clicado () : void{
            this.$emit('clicado')
        }
    }
})
</script>