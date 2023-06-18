<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <Cronometro :temporizador="temporizador"/>
                    <button class="button" @click="iniciar()" :disabled="cronometroRodando">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="finalizar()" :disabled="!cronometroRodando">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>
                </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Cronometro from './Cronometro.vue';

export default defineComponent({
    name: 'TemporizadorComponent',
    components:{
        Cronometro
    },
    data() {
        return {
            temporizador: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
   emits:['temporizadorFinalizado'],
    methods: {
        iniciar() {
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                this.temporizador++;
            }, 1000)
        },
        finalizar() {
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('temporizadorFinalizado', this.temporizador)
            this.temporizador = 0
        },
    }
})
</script>