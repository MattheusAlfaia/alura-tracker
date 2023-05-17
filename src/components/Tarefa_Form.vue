<template>
    <Box_Form>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao ? tarefa.descricao : 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <Cronometro_form :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </Box_Form>
</template>

<script lang="ts">
import { defineComponent, PropType} from 'vue';
import Cronometro_form from './Cronometro_Form.vue';
import ITarefa from './Interfaces/Interface';
import Box_Form from './Box_Form.vue';

export default defineComponent({
    name: 'Tarefa_Form',
    components: {
        Cronometro_form,
        Box_Form
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
});
</script>