<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa.">
                <input  type="text" class="input" placeholder="Qual tarefa você deseja iniciar"/>    
            </div>
            <div class="column">
                <TemporizadorTask @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TemporizadorTask from './TemporizadorTask.vue';

export default defineComponent({
    name: 'FormularioTask',
    components: {
        TemporizadorTask
    },
    data () {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number): void {
            this.descricao = ''
        }
    }
    
})

</script>