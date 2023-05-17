<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro' : modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <Barra_Lateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario_Form @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Tarefa_Form v-for="(tarefa, index) in tarefas" :tarefa="tarefa" :key="index"/>
        <Box_Form v-if="listaEstaVazia">
          Você Não tem nenhuma tarefa :(
        </Box_Form>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Barra_Lateral from './components/Barra_Lateral.vue';
import Formulario_Form from './components/Formulario_Form.vue';
import Tarefa_Form from './components/Tarefa_Form.vue';
import ITarefa from './components/Interfaces/Interface';
import Box_Form from './components/Box_Form.vue';

export default defineComponent({
  name: 'App',
  components: {
    Barra_Lateral,
    Formulario_Form,
    Tarefa_Form,
    Box_Form
  },
  data(){
    return{
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  computed:{
    listaEstaVazia() : boolean{
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa){
      this.tarefas.push(tarefa);
    },
    trocarTema (modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo;
    }
  }
});
</script>

<style>
.lista {
  padding:  1.25rem;
}
main{
  --bg-primary: #fff;
  --text-primary: #000;
}
main.modo-escuro{
  --bg-primary: #2b2d42;
  --text-primary: #ddd;
}
.conteudo{
  background-color: var(--bg-primary);
}
</style>
