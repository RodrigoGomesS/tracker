<template>
    <section>
      <strong>
             {{ tempoDecorrido }}
      </strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'CronometroComponent',
    props:{
        temporizador: {
            type: Number,
            default: 0
        }
    },
    computed: {
        tempoDecorrido(): string {
            return new Date(this.temporizador * 1000).toISOString().slice(11, 19)
        }
    },
});
</script>