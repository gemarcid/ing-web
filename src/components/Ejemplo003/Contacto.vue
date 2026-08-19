<template>
  <section class="contacto">
    <form class="formulario" novalidate @submit.prevent="validarFormulario">
      <label>
        Nombre
        <input v-model.trim="nombre" type="text" placeholder="Nombre" />
      </label>

      <label>
        Correo
        <input v-model.trim="correo" type="email" placeholder="Correo" />
      </label>

      <label>
        Teléfono
        <input v-model.trim="telefono" type="tel" placeholder="Teléfono" />
      </label>

      <label>
        Mensaje
        <textarea v-model.trim="mensaje" placeholder="Mensaje"></textarea>
      </label>

      <label class="newsletter">
        <input v-model="newsletter" type="checkbox" />
        Suscribirse al boletín
      </label>

      <button type="submit">Enviar</button>
    </form>

    <p v-if="error" class="error" role="alert">{{ error }}</p>

    <div v-if="enviado" class="datos" aria-live="polite">
      <h2>Datos enviados:</h2>
      <p><strong>Nombre:</strong> {{ nombre }}</p>
      <p><strong>Correo:</strong> {{ correo }}</p>
      <p><strong>Teléfono:</strong> {{ telefono }}</p>
      <p><strong>Mensaje:</strong> {{ mensaje }}</p>
      <p><strong>Boletín:</strong> {{ newsletter ? 'Sí' : 'No' }}</p>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Contacto',
  data() {
    return {
      nombre: '',
      correo: '',
      telefono: '',
      mensaje: '',
      newsletter: false,
      enviado: false,
      error: ''
    }
  },
  methods: {
    validarFormulario() {
      if (!this.nombre || !this.correo || !this.telefono || !this.mensaje) {
        this.enviado = false
        this.error = 'Todos los campos son obligatorios'
        return
      }

      this.enviado = true
      this.error = ''
    }
  }
}
</script>

<style scoped>
.contacto {
  width: min(calc(100% - 1rem), 22rem);
  margin: auto;
  padding: 1rem;
  box-sizing: border-box;
  text-align: left;
}

.formulario,
.formulario label {
  display: grid;
  gap: 0.5rem;
}

.formulario {
  gap: 0.55rem;
}

.formulario label {
  color: #1e3a5f;
  font-size: 0.9rem;
  font-weight: 600;
}

input,
textarea {
  box-sizing: border-box;
  width: 100%;
  padding: 0.45rem 0.6rem;
  border: 1px solid #93c5fd;
  border-radius: 0.5rem;
  color: #1e3a5f;
  background: #eff6ff;
  font: inherit;
}

textarea {
  min-height: 4rem;
  resize: vertical;
}

input:focus,
textarea:focus {
  outline: 3px solid #bfdbfe;
  border-color: #60a5fa;
}

.formulario .newsletter {
  display: flex;
  align-items: center;
  font-weight: 400;
}

.newsletter input {
  width: auto;
}

button {
  padding: 0.45rem 0.85rem;
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

.error,
.datos {
  margin-top: 0.8rem;
  padding: 0.75rem;
  border-radius: 0.5rem;
}

.error {
  border: 1px solid #fca5a5;
  color: #991b1b;
  background: #fee2e2;
}

.datos {
  border: 1px solid #93c5fd;
  color: #1e3a5f;
  background: #dbeafe;
}

.datos h2 {
  margin: 0 0 0.75rem;
  color: #1e3a5f;
  font-size: 1.25rem;
}

.datos p + p {
  margin-top: 0.4rem;
}
</style>
