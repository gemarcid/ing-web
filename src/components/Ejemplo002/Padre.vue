<template>
  <main class="actividad">
    <HijoBoton @saludo="mostrarSaludo" />

    <p v-if="mensaje" class="mensaje" role="status">
      {{ mensaje }}
    </p>
  </main>
</template>

<script>
import HijoBoton from './HijoBoton.vue'

export default {
  name: 'PadreEjemplo002',
  components: {
    HijoBoton
  },
  data() {
    return {
      mensaje: ''
    }
  },
  methods: {
    mostrarSaludo() {
      this.mensaje = 'Hola desde el hijo'
    }
  }
}
</script>

<style scoped>
.actividad {
  display: grid;
  justify-items: center;
  gap: 1.5rem;
  margin: auto;
  padding: 2rem;
}

.mensaje {
  padding: 1rem 1.25rem;
  border: 1px solid #93c5fd;
  border-radius: 0.5rem;
  color: #1e3a5f;
  background: #dbeafe;
}
</style>
