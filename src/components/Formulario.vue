<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" area-label="Formulário para criação de uma noa tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja incluir?">
            </div>
            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <section>
                        <strong>{{ tempoDecorrido }}</strong>
                    </section>
                    <button class="button" @click="iniciar()">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="finalizar()">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'FormularioForm',
    data() {
        return {
            temporizador: 0,
            cronometro: 0
        }
    },
    computed: {
        tempoDecorrido(): string {
            return new Date(this.temporizador * 1000).toISOString().slice(11, 19)
        }
    },
    methods: {
        iniciar() {
            console.log('iniciar')
            this.cronometro = setInterval(() => {
                this.temporizador++;
            }, 1000)
        },
        finalizar() {
            clearInterval(this.cronometro)
        },
    }
})
</script>

<style scoped></style>