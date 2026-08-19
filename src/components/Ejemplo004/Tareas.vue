<template>
  <main class="tareas">
    <div class="nueva-tarea">
      <input
        v-model.trim="nuevaTarea"
        type="text"
        placeholder="Escribe una nueva tarea"
        aria-label="Nueva tarea"
        @keyup.enter="agregarTarea"
      />
      <button type="button" @click="agregarTarea">Agregar</button>
    </div>

    <button class="alternar" type="button" @click="mostrar = !mostrar">
      {{ mostrar ? 'Ocultar' : 'Mostrar' }} tareas
    </button>

    <ul v-show="mostrar && tareas.length" class="lista">
      <li v-for="(t, index) in tareas" :key="index">
        <span>{{ t }}</span>
      </li>
    </ul>

    <p v-if="mostrar && tareas.length === 0" class="vacio">
      No hay tareas registradas
    </p>
  </main>
</template>

<script>
export default {
  data() {
    return {
      nuevaTarea: '',
      tareas: [],
      mostrar: true
    }
  },
  methods: {
    agregarTarea() {
      if (this.nuevaTarea) {
        this.tareas.push(this.nuevaTarea);
        this.nuevaTarea = '';
      }
    }
  }
}
</script>


<style scoped>
.tareas {
  box-sizing: border-box;
  width: min(calc(100% - 2rem), 28rem);
  margin: clamp(1rem, 8vh, 4rem) auto;
  padding: clamp(1rem, 4vw, 1.5rem);
  border: 1px solid #bfdbfe;
  border-radius: 0.9rem;
  background: #eff6ff;
  box-shadow: 0 8px 24px #1e3a5f14;
}

.nueva-tarea {
  display: grid;
  grid-template-columns: minmax(0, 1fr) auto;
  gap: 0.6rem;
}

input {
  box-sizing: border-box;
  min-width: 0;
  width: 100%;
  padding: 0.6rem 0.75rem;
  border: 1px solid #93c5fd;
  border-radius: 0.5rem;
  color: #1e3a5f;
  background: #fff;
  font: inherit;
}

input:focus {
  border-color: #60a5fa;
  outline: 3px solid #bfdbfe;
}

button {
  padding: 0.6rem 0.9rem;
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

.alternar {
  width: 100%;
  margin-top: 0.75rem;
  background: #dbeafe;
}

.lista {
  display: grid;
  gap: 0.5rem;
  margin: 1rem 0 0;
  padding: 0;
  list-style: none;
  text-align: left;
}

.lista li {
  padding: 0.65rem 0.8rem;
  border: 1px solid #bfdbfe;
  border-radius: 0.5rem;
  color: #1e3a5f;
  background: #fff;
  overflow-wrap: anywhere;
}

.vacio {
  margin-top: 1rem;
  color: #64748b;
  font-size: 0.9rem;
}

@media (max-width: 420px) {
  .nueva-tarea {
    grid-template-columns: 1fr;
  }
}
</style>
