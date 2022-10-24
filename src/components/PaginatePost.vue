<script setup>
//se reciben los props de app vue:
defineProps( ["inicio", "fin", "maxLength"] )

//Se recomienda esta opcion en VUE
const emit = defineEmits(['next', 'prev'])

//pruebas un Metodo
const activarçSiguiente = () => {
    console.log('me diste a siguiente')
    emit("next")
}

</script>
<template lang="">
<div class="btn-group" role="group" aria-label="Basic example">
  <button 
    @click="emit('prev')" 
    type="button" 
    class="btn btn-outline-primary"
    :disabled="inicio === 0">
    Previus {{inicio}}
</button>
  <button 
    @click="activarçSiguiente" 
    type="button" 
    class="btn btn-outline-primary"
    :disabled="fin >= maxLength">
    Next {{fin}}
</button>
</div>
</template>
