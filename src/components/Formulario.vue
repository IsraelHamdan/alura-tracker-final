<template>
   <div class="box form">
      <div class="columns is-8" role="form" aria-label="formulário para criação de uma nova tarefa">
         <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model ="descricao " >
      </div>
      <div class="colum">
         <Temporizador @aoTemporizadorFinalizado ="finalizarTarefa"/>  
      </div>
   </div>
</template>

<script lang="ts"> 
import { defineComponent } from 'vue';
import Temporizador from './Temporizador.vue';
export default defineComponent({
   emits: ['aoSalvarTarefa'],
   name:'Formulário',
   components: {
      Temporizador
   },
   data() {
      return {
         descricao: ''
      }
   },
   methods: {
      finalizarTarefa(tempoDecorrido: number) :void {
         this.$emit('aoSalvarTarefa', {
            duracaoEmSegundos: tempoDecorrido, descricao:this.descricao
         })
         this.descricao = ''
      }
   }
})
</script>
<style>
.form {
   color: var(--texto-primario);
   background-color: var(--bg-primario);
}
</style>