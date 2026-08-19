<template>
  <div>
    <Hijo mensaje="Hola desde el padre" />
  </div>
</template>
<script>
import Hijo from './Ejemplo001/Hijo.vue/index.js'
export default {
  components: {
    Hijo
  }
}
</script>