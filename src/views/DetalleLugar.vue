<template>
  <div>
    <h2>Detalle de {{ lugar.nombre }}</h2>
    <p>Clima actual: {{ lugar.clima }}</p>

    <!-- Pronóstico de varios días -->
    <h3>Pronóstico semanal</h3>
    <ul>
      <li v-for="(dia, index) in lugar.pronostico" :key="index">
        {{ dia.dia }}: {{ convertirTemperatura(dia.temp) }}°{{ unidad }}
      </li>
    </ul>

    <!-- Estadísticas semanales -->
    <h3>Estadísticas</h3>
    <p v-if="estadisticas">
      Mín: {{ convertirTemperatura(estadisticas.min) }}°{{ unidad }} <br>
      Máx: {{ convertirTemperatura(estadisticas.max) }}°{{ unidad }} <br>
      Promedio: {{ convertirTemperatura(estadisticas.promedio) }}°{{ unidad }}
    </p>

    <!-- Botón para volver -->
    <router-link to="/">Volver al Home</router-link>
  </div>
</template>

<script>
export default {
  name: 'DetalleLugar',
  props: ['id'],
  data() {
    return {
      unidad: 'C',
      lugares: [
        { 
          id: 1, nombre: 'Playa Azul', clima: 'Soleado',
          pronostico: [
            { dia: 'Lunes', temp: 30 },
            { dia: 'Martes', temp: 32 },
            { dia: 'Miércoles', temp: 28 },
            { dia: 'Jueves', temp: 29 },
            { dia: 'Viernes', temp: 31 }
          ]
        },
        { 
          id: 2, nombre: 'Montaña Verde', clima: 'Nublado',
          pronostico: [
            { dia: 'Lunes', temp: 18 },
            { dia: 'Martes', temp: 20 },
            { dia: 'Miércoles', temp: 17 },
            { dia: 'Jueves', temp: 19 },
            { dia: 'Viernes', temp: 21 }
          ]
        },
        { 
          id: 3, nombre: 'Ciudad Roja', clima: 'Lluvioso',
          pronostico: [
            { dia: 'Lunes', temp: 22 },
            { dia: 'Martes', temp: 23 },
            { dia: 'Miércoles', temp: 21 },
            { dia: 'Jueves', temp: 20 },
            { dia: 'Viernes', temp: 24 }
          ]
        },
        { 
          id: 4, nombre: 'Valle Dorado', clima: 'Despejado',
          pronostico: [
            { dia: 'Lunes', temp: 25 },
            { dia: 'Martes', temp: 26 },
            { dia: 'Miércoles', temp: 24 },
            { dia: 'Jueves', temp: 27 },
            { dia: 'Viernes', temp: 28 }
          ]
        },
        { 
          id: 5, nombre: 'Isla Blanca', clima: 'Ventoso',
          pronostico: [
            { dia: 'Lunes', temp: 28 },
            { dia: 'Martes', temp: 29 },
            { dia: 'Miércoles', temp: 27 },
            { dia: 'Jueves', temp: 30 },
            { dia: 'Viernes', temp: 31 }
          ]
        }
      ]
    }
  },
  computed: {
    lugar() {
      return this.lugares.find(l => l.id == this.id)
    },
    estadisticas() {
      if (!this.lugar) return null
      const temps = this.lugar.pronostico.map(d => d.temp)
      const min = Math.min(...temps)
      const max = Math.max(...temps)
      const promedio = temps.reduce((a, b) => a + b, 0) / temps.length
      return { min, max, promedio }
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