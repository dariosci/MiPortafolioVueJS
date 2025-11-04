<script setup>
import { ref } from 'vue';
import FondoDinamico from './FondoDinamico.vue';

const interesesList = ref([]);
interesesList.value = ([
  'Me apasiona comprender el funcionamiento interno de los sistemas operativos, desde la gestión de procesos y memoria hasta la interacción con el hardware. Me interesa especialmente cómo los diferentes sistemas - como Linux, Windows y macOS - abordan la administración de recursos y la seguridad, y disfruto experimentar con entornos virtualizados y configuraciones avanzadas.',
  'La programación es mi herramienta principal para crear soluciones y automatizar tareas. Disfruto escribir código limpio y estructurado, probar nuevas tecnologías y aprender distintos lenguajes de programación. Me atrae especialmente el desarrollo de aplicaciones prácticas que integren lógica, diseño y funcionalidad real.',
  'Tengo gran interés en el diseño, configuración y mantenimiento de redes informáticas. Me gusta trabajar con conceptos como direccionamiento IP, protocolos de comunicación, VLANs y VPNs. También disfruto analizar el rendimiento y la seguridad de las redes, aplicando tanto teoría como práctica en entornos simulados y reales.',
  'En mis ratos libres, me gusta jugar videojuegos, no solo por entretenimiento sino también porque me inspiran a entender cómo se combinan la programación, el diseño gráfico y la interacción con el usuario. Además, me ayudan a desarrollar pensamiento estratégico, trabajo en equipo y toma de decisiones rápida.']);
</script>

<template>
  <div class="intereses">
  <FondoDinamico /> <!-- Efecto de fondo -->
  <div class="contenido">
    <ul>
      <li class="item" v-for="interes in interesesList" :key="interes">
        {{ interes }}
      </li>
    </ul>
  </div>
</div>

</template>

<style scoped>
.intereses {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 2rem;
  margin-top: 32px;
  margin-bottom: 32px;
  min-height: 600px;
  overflow: hidden; /* Evita desbordes */
  border-radius: 10px;
}

.contenido {
  position: relative;
  z-index: 2; /* Por encima del fondo animado */
  color: white;
}

.text-gray-800 {
  color: #ffffff;
}

.item {
  margin-bottom: 1rem;
  font-size: 1.1rem;
  line-height: 1.6;
  text-align: center;
}
</style>
