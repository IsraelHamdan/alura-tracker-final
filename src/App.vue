<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuroAtivo}" >
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvaTarefa" />
      <div class="lista">
        <Box v-if="listaVazia">
          Vamos começar a produzir, rumo ao sucesso, let's bora :)
        </Box>
        <Tarefa  v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import Formulario from './components/Formulario.vue';
import Tarefa from './components/Tarefa.vue';
import Box from './components/Box.vue';
import ITarefa from './interfaces/ITarefa'
export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario, 
    Tarefa,
    Box
  },
  data () {
    return {
      tarefas: [] as ITarefa[], 
      modoEscuroAtivo: false
    }
  }, 
  computed: {
    listaVazia () :boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvaTarefa (tarefa: ITarefa){
      this.tarefas.push(tarefa)
    },
    trocarTema (modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>
<style>
.lista {
  padding: 1.25rem;
}
main {
  --bg-primario: #fff;
  --txt-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --txt-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
