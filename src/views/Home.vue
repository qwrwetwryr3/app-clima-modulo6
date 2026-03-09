<template>
  <div>
    <h2>Lista de lugares</h2>

    <!-- Selector de unidad de temperatura -->
    <label>
      Unidad:
      <select v-model="unidad">
        <option value="C">°C</option>
        <option value="F">°F</option>
      </select>
    </label>

    <!-- Input de búsqueda -->
    <input 
      type="text" 
      v-model="busqueda" 
      placeholder="Buscar lugar..." 
    />

    <!-- Lista filtrada -->
    <ul>
      <li v-for="lugar in lugaresFiltrados" :key="lugar.id">
        <router-link :to="`/lugar/${lugar.id}`">
          {{ lugar.nombre }} - {{ convertirTemperatura(lugar.temp) }}°{{ unidad }}
        </router-link>
      </li>
    </ul>

    <p v-if="lugaresFiltrados.length === 0">No se encontró el lugar</p>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      busqueda: '',
      unidad: 'C',
      lugares: [
        { id: 1, nombre: 'Playa Azul', temp: 30 },
        { id: 2, nombre: 'Montaña Verde', temp: 18 },
        { id: 3, nombre: 'Ciudad Roja', temp: 22 },
        { id: 4, nombre: 'Valle Dorado', temp: 25 },
        { id: 5, nombre: 'Isla Blanca', temp: 28 }
      ]
    }
  },
  computed: {
    lugaresFiltrados() {
      return this.lugares.filter(lugar =>
        lugar.nombre.toLowerCase().includes(this.busqueda.toLowerCase())
      )
    }
  },
  methods: {
    convertirTemperatura(tempC) {
      return this.unidad === 'C' 
        ? tempC 
        : Math.round((tempC * 9/5) + 32)
    }
  }
}
</script>