<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const estudios = ref([]);
estudios.value = [
  { id: 1, fecha: "1994", color: "#25CA33FF", titulo: "Operador de PC", institucion: "Colegio 65-p ECEA", totalHoras: "48" },
  { id: 2, fecha: "1997", color: "#FBCA3E", titulo: "MS Works para Windows", institucion: "Centro de Capacitación para el trabajo Nº 6-205", totalHoras: "40" },
  { id: 3, fecha: "1998", color: "#E24A68", titulo: "MS Office 97", institucion: "Centro de Capacitación para el Trabajo N° 6-205", totalHoras: "48" },
  { id: 4, fecha: "2000", color: "#1B5F8C", titulo: "MS Office 2000", institucion: "Centro de Capacitación para el Trabajo N° 6-205", totalHoras: "56" },
  { id: 5, fecha: "2001", color: "#4CADAD", titulo: "Ingeniería en Software (3er Año Cursado)", institucion: "Universidad del Aconcagua", totalHoras: "3 años" },
  { id: 6, fecha: "2022", color: "#25CA33FF", titulo: "#SeProgramar", institucion: "Argentina Programa 4.0 - INTI - Ministerio de Economía de la Nación", totalHoras: "60" },
  { id: 7, fecha: "2022", color: "#FBCA3E", titulo: "Curso Programación PYTHON", institucion: "Fundación Educativa Santísima Trinidad - Ministerio de Economía y Energia - Gobierno de Mendoza", totalHoras: "-" },
  { id: 8, fecha: "2022", color: "#E24A68", titulo: "Python 101 fot Data Science", institucion: "Cognitive Class.ai - Powered by IBM", totalHoras: "300" },
  { id: 9, fecha: "2023", color: "#1B5F8C", titulo: "Primeros pasos del desarrollo frontend", institucion: "Argentina Programa 4.0 - Ticmas - Ministerio de Economía de la Nación", totalHoras: "60" },
  { id: 10, fecha: "2023", color: "#4CADAD", titulo: "MS-AZ-800.ADMINISTERING WINDOWS SERVER HYBRID CORE INFRASTRUCTURE", institucion: "EXO Training Center - División Educación EXO S.A.", totalHoras: "-" },
  { id: 11, fecha: "2023", color: "#25CA33FF", titulo: "Desarrollo de Aplicaciones Móviles", institucion: "Argentina Programa 4.0 - Ticmas - Ministerio de Economía de la Nación", totalHoras: "-" },
  { id: 12, fecha: "2023", color: "#FBCA3E", titulo: "CURSO INGLÉS TIC NIVEL 1 - Traducción desde la gramática estructural", institucion: "Fundación Educativa Santísima Trinidad - Ministerio de Economía y Energia - Gobierno de Mendoza", totalHoras: "63" },
  { id: 13, fecha: "2023", color: "#E24A68", titulo: "CURSO INGLÉS TIC NIVEL 2 - Competencias comunicativas: desde la expresión personal a la comunicación del rol profesional", institucion: "Fundación Educativa Santísima Trinidad - Ministerio de Economía y Energia - Gobierno de Mendoza", totalHoras: "63" },
  { id: 14, fecha: "2023", color: "#1B5F8C", titulo: "CURSO INGLÉS TIC NIVEL 3 - “El proceso comunicativo en el rol profesional", institucion: "Fundación Educativa Santísima Trinidad - Ministerio de Economía y Energia - Gobierno de Mendoza", totalHoras: "84" },
  { id: 15, fecha: "2025", color: "#4CADAD", titulo: "Tecnicatura Universitaria en Programación", institucion: "UTN Regional San Rafael", totalHoras: "Presente" }
];

const timelineRefs = ref([]);
const visibleItems = ref(new Set());

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        const index = timelineRefs.value.indexOf(entry.target);
        if (entry.isIntersecting && index !== -1) {
          visibleItems.value.add(index);
        }
      });
    },
    { threshold: 0.2 }
  );

  timelineRefs.value.forEach((el) => observer.observe(el));

  onBeforeUnmount(() => observer.disconnect());
});
</script>

<template>
  <section id="estudios" class="py-16 bg-gray-50">
    <h2 class="text-4xl font-bold text-center text-gray-800 mb-12">
      Estudios
    </h2>

    <div class="relative max-w-6xl mx-auto px-10">
      <!-- Línea central -->
      <div class="absolute left-1/2 transform -translate-x-1/2 h-full w-1 bg-gradient-to-b from-blue-300 to-cyan-400">
      </div>

      <!-- Ítems -->
      <div v-for="(item, index) in estudios" :key="item.id"
        class="relative flex flex-col md:flex-row items-center mb-2 opacity-0 translate-y-10 transition-all duration-700 ease-out"
        :class="[
          index % 2 === 0 ? 'md:flex-row-reverse' : '',
          visibleItems.has(index) ? 'opacity-100 translate-y-0' : ''
        ]" ref="timelineRefs">
        <!-- 📱 Fecha arriba solo en móvil -->
        <div class="block md:hidden mb-4 text-center">
          <span class="fecha font-bold text-lg tracking-wide" :style="{ backgroundColor: item.color }">
            {{ item.fecha }}
          </span>
        </div>
        <!-- Contenido -->
        <div
          class="bg-white shadow-xl rounded-2xl p-6 w-full md:w-[42%] z-10 transition-transform duration-300 hover:scale-105 hover:shadow-2xl"
          :class="index % 2 === 0 ? 'md:ml-16' : 'md:mr-16'">
          <h3 class="text-xl font-semibold mb-1" :style="{ color: item.color }">
            {{ item.titulo }}
          </h3>
          <p class="text-gray-600 font-medium">{{ item.institucion }}</p>
          <p class="text-sm text-gray-400 mt-2">
            Total horas: {{ item.totalHoras }}
          </p>
        </div>

        <!-- Punto central (solo en escritorio) -->
        <div
          class="absolute left-1/2 transform -translate-x-1/2 w-8 h-8 rounded-full border-4 border-white shadow-md flex items-center justify-center hidden md:flex"
          :style="{ backgroundColor: item.color }"></div>

        <!-- Fecha normal en escritorio -->
        <div class="hidden md:block text-center mb-2"
          :class="index % 2 === 0 ? 'md:text-right md:pr-10' : 'md:text-left md:pl-10'">
          <span class="font-bold text-lg tracking-wide" :style="{ color: item.color }">
            {{ item.fecha }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.estudios {
  display: flex;
  justify-content: center;
  margin-bottom: 3rem;
}

.container-estudios {
  display: flex;
  width: 100%;
  line-height: 2.5rem;
  font-size: large;
}

section {
  animation: fadeIn 0.6s ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.bg-gray-50 {
  --tw-bg-opacity: 1;
  background-color: rgb(24 24 24 / var(--tw-bg-opacity, 1));
}

.text-gray-800 {
  --tw-text-opacity: 1;
  color: #FFFFFF;
}

.py-16 {
  padding-top: 32px !important;
  padding-bottom: 32px !important;
}

/* Moviles (Pantallas pequeñas, hasta 767px) */
@media (max-width: 767px) {

  /* Línea central más corta: empieza en el primer punto */
  #estudios .relative>.absolute.bg-gradient-to-b {
    top: 40px;
    /* ajusta según la distancia del primer punto */
    height: calc(100% - 40px);
  }

  /* Achicar un poco las tarjetas */
  #estudios .bg-white {
    transform: scale(0.9);
    margin: 0 auto 1rem auto;
  }

  /* Alinear el año arriba de la tarjeta */
  #estudios .font-bold.text-lg {
    margin-bottom: 0.5rem;
  }

  /* Agregando el responsivo para la seccion estudios */
  .container-estudios {
    width: 100%;
    margin: 0rem;
  }

  .estudios {
    width: 100%;
    margin-top: 1rem;
    font-size: small;
  }

  .img-estudios {
    width: 25%;
    height: auto;
    border-radius: 0.5rem;
  }

  .detalle-estudios {
    color: var(--black2);
    font-size: 15px;
    line-height: 32px;
    margin-bottom: auto;
  }

  .link-icono {
    font-size: 1em;
  }

  .instituto-class {
    font-style: italic;
  }

  .timeline-line {
    top: 80px;
    /* empieza un poco más abajo, desde la primera fecha */
    bottom: 0;
  }

  .fecha {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    color: white;
    font-weight: bold;
    text-shadow: 0 0 5px rgba(0, 0, 0, 0.8);
    font-size: 1rem;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.4);
    transition: transform 0.3s ease;
  }

  .fecha:hover {
    transform: scale(1.1);
  }
}

/* Tablets (Pantallas medianas, entre 768px y 1023px) */
@media (min-width: 768px) and (max-width: 1023px) {

  /* Agregando el responsivo para seccion estudios */
  .estudios {
    width: 100%;
  }

  #tabla-cursos th:nth-child(2),
  #tabla-cursos th:nth-child(3),
  #tabla-cursos td:nth-child(2),
  #tabla-cursos td:nth-child(3) {
    font-size: medium;
  }

  td {
    font-size: medium;
  }

  th {
    font-size: large;
  }
}

/* Escritorio (Pantallas anchas, a partir de 1024px) */
@media (min-width: 1024px) {

  /* Agregando el responsivo para seccion estudios */
  .estudios {
    width: 100%;
  }

  .container-estudios-section {
    display: flex;
    align-items: center;
    width: 100%;
    gap: 2rem;
  }

  th {
    font-size: large;
  }

  td {
    font-size: large;
  }
}
</style>
