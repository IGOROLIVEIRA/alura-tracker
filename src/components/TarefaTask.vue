<template>
    <BoxTask>
        <div class="columns">
            <div class="column is-7">{{ tarefa.descricao || 'Tarefa sem descrição' }} </div>
            <div class="column">
                <CronometroTask :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxTask>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroTask from './CronometroTask.vue';
import ITarefa from '../interfaces/ITarefa';
import BoxTask from './BoxTask.vue';

export default defineComponent({
    name: 'TarefaTask',
    components: {
        CronometroTask,
        BoxTask
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>