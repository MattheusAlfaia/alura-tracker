<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário Cria Tarefa">
                <input type="text"
                 class="input" 
                 placeholder="Qual tarefa deseja iniciar?"
                 v-model="descricao"
                 >
            </div>
            <div class="column">
                <Temporizador_Form @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Temporizador_Form from './Temporizador_Form.vue';

export default defineComponent({
    name: 'Formulario_Form',
    emits:['aoSalvarTarefa'],
    components: {
        Temporizador_Form
    },
    data(){
        return{
            descricao: ''
        }
    },
    methods:{
        finalizarTarefa(tempoDecorrido: number) : void{
            this.$emit('aoSalvarTarefa',{
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            })
            this.descricao = '';            
        }
    }
});
</script>

<style>
.formulario{
    color: var(--text-primary);
    background: var(--bg-primary);
}
</style>