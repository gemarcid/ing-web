<template>
  <button type="button" @click="$emit('saludo')">
    Enviar saludo
  </button>
</template>

<script>
export default {
  name: 'HijoBoton',
  emits: ['saludo']
}
</script>

<style scoped>
button {
  padding: 0.75rem 1.25rem;
  border: 0;
  border-radius: 0.5rem;
  color: #1e3a5f;
  background: #bfdbfe;
  font: inherit;
  font-weight: 600;
  cursor: pointer;
}

button:hover {
  background: #93c5fd;
}

button:focus-visible {
  outline: 3px solid #93c5fd;
  outline-offset: 3px;
}
</style>
