<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroTask :tempoEmSegundos="tempoEmSegundos" />
    <BotaoTask @clicado="iniciar" icone="fas fa-play" texto="Play" :desabilitado="cronometroRodando"/>
    <BotaoTask @clicado="finalizar" icone="fas fa-stop" texto="Stop" :desabilitado="!cronometroRodando"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTask from './CronometroTask.vue';
import BotaoTask from './BotaoTask.vue';

export default defineComponent({
    name: "TemporizadorTask",
    emits: ['aoTemporizadorFinalizado'],
    components: { CronometroTask, BotaoTask},
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        };
    },
    methods: {
        iniciar() {
            this.cronometroRodando = true;
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000);
        },
        finalizar() {
            this.cronometroRodando = false;
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0;
        }
    },
})

</script>