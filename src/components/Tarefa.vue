<template>
   <Box>
      <div class="coluns">
         <div class="coluns is-7">
            {{ tarefa?.descricao || 'Tarefa sem descrição' }}
         </div>
         <div class="coluns">
            <Cronometro :tempoEmSegundos="tarefa?.duracaoEmSegundos" />
         </div>
      </div>
   </Box>
</template>

<script lang="ts">
import { defineComponent, PropType} from 'vue';
import Cronometro from './Cronometro.vue';
import Box from './Box.vue';
import ITarefa from '../interfaces/ITarefa';

export default defineComponent({
   name: 'Tarefa',
   components: {
      Cronometro,
      Box
   },
   props: {
      tarefa: {
         type: Object as PropType<ITarefa>,
         require: true
      }
   }
})
</script>
