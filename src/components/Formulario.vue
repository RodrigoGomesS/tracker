<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" area-label="Formulário para criação de uma noa tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja incluir?" v-model="descricao">
            </div>
            <div class="column">
                <Temporizador @temporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Temporizador from './Temporizador.vue';

export default defineComponent({
    name: 'FormularioForm',
    components:{
       Temporizador
    },
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(temporizador : number) :void{
            console.log(temporizador)
            console.log(this.descricao)
            this.descricao = ''
        }
    },
})
</script>

<style scoped></style>