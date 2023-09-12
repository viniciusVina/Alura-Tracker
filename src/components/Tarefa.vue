<template>
    <div class="column">
        <Box>
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem Descrição' }}
            </div>
            <div class="column">
                <Cronometro :tempoemsegundos="tarefa.duracaoEmSegundos" />

            </div>
        </Box>

    </div>
</template>


<script lang="ts">

import { defineComponent, PropType } from 'vue';
import Cronometro from './Cronometro.vue';
import Itarefa from '@/Interfaces/Itarefa';
import Box from './Box.vue';

export default defineComponent({

    name: 'tarefa-app',
    components: {
        Cronometro,
        Box
    },
    props: {
        tarefa: {
            type: Object as PropType<Itarefa>,
            required: true
        }
    }


})

</script>

