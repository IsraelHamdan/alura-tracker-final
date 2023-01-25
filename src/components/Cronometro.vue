<template>
   <section>
      <strong class="display">
         {{ tempoDecorrido }}
      </strong>
      </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
   name: 'Cronometro', 
   props: {
      tempoEmSegundos: {
         type: Number,
         default: 0, 
         required: true 
      }
  },
   computed: {
      tempoDecorrido () :string {
         return new Date(this.tempoEmSegundos * 1000).toISOString().substring(19, 11);
      }
   },
})

</script>

<style scoped>
.display {
   color: var(--txt-primario)
}
</style>