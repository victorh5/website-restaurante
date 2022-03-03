<script setup lang="ts">
const emits = defineEmits(['make_order', 'cancel_order'])
</script>

<template>
  <div class="acoes-pedido">
    <button @click="emits('make_order')">Realizar Pedido</button>
    <button @click="emits('cancel_order')">Cancelar Pedido</button>
  </div>
</template>