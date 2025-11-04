<script setup>
import { ref } from 'vue';
// Importar todas las imágenes de la carpeta
const logos = import.meta.glob('../assets/images/*', { eager: true, import: 'default', query: '?url' });

const experiencia = ref([]);
experiencia.value = [
  {
    id: 0,
    logo: logos['../assets/images/logo-hosp-392x84.png'],
    nombre: 'Hospital Grl. Las Heras - Tupungato',
    periodo: 'Marzo 2018-Presente',
    cargo: 'Servicio de Computos: Analista Mayor',
    url: 'https://hosplasheras.mendoza.gov.ar/'
  },
  {
    id: 0,
    logo: logos['../assets/images/SciliTec-Logo-chico.png'],
    nombre: 'Scilitec',
    periodo: 'Abril 2017-Presente',
    cargo: 'Emprendimiento Propio',
    url: 'https://www.facebook.com/scilitec'
  },
];
</script>

<template>
  <section id="experiencia" class="experiencia">
    <div class="container">

      <div class="categoria_icono">
        <!--<i class="fa-solid fa-city"></i>-->
        <h2 class="text-4xl font-bold text-center text-gray-800 mb-12">Experiencia Laboral</h2>
      </div>

      <article class="container-experiencia" id="container-experiencia">
        <div class="tarjeta-experiencia" v-for="item in experiencia" :key="item.id">
          <div class="experiencia-logo">
            <a :href="item.url" target="_blank">
              <img :src=item.logo :alt="item.nombre" srcset="" />
            </a>
          </div>
          <div class="experiencia-contenido">
            <p class="experiencia-periodo">{{ item.periodo }}</p>
            <h4 class="experiencia-cargo">{{ item.cargo }}</h4>
          </div>
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.experiencia {
  display: flex;
  justify-content: center;
  margin-top: 32px;
}

.container-experiencia {
  display: flex;
  width: 100%;
  line-height: 2.5rem;
  font-size: large;
  flex-direction: column;
}

.mb-12 {
  margin-bottom: 24px !important;
}

/* Estilos generales para las tarjetas de experiencia */
.tarjeta-experiencia {
  display: flex;
  /* Habilitamos Flexbox para alinear los elementos internos */
  align-items: center;
  /* Centra verticalmente el logo y el contenido */
  background-color: rgb(189, 186, 186);
  /* Fondo de la tarjeta, ajusta a tu paleta */
  border-radius: 8px;
  /* Bordes redondeados */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  /* Sombra suave para darle profundidad */
  padding: 20px;
  /* Espaciado interno */
  margin-bottom: 20px;
  /* Espacio entre tarjetas */
  gap: 20px;
  /* Espacio entre el logo y el contenido (Flexbox gap) */
  flex-wrap: wrap;
  /* Permite que los elementos se envuelvan en pantallas pequeñas */
}

/* Estilos para el contenedor del logo */
.experiencia-logo {
  flex-shrink: 0;
  /* Evita que el logo se encoja */
  width: 20rem;
  /* Ancho fijo para el contenedor del logo */
  height: auto;
  /* Alto fijo para el contenedor del logo */
  display: flex;
  justify-content: center;
  align-items: center;
  /* Opcional: Si quieres un fondo para el logo */
  /* background-color: #f0f0f0; */
  /* border-radius: 50%; */
}

.experiencia-logo img {
  max-width: 100%;
  /* Asegura que la imagen no exceda el ancho de su contenedor */
  max-height: 100%;
  /* Asegura que la imagen no exceda el alto de su contenedor */
  object-fit: contain;
  /* Ajusta la imagen dentro del contenedor sin recortar */
  border-radius: 4px;
  /* Opcional: si el logo tiene bordes cuadrados */
}

/* Estilos para el contenedor del contenido (periodo y cargo) */
.experiencia-contenido {
  flex-grow: 1;
  /* Permite que el contenido ocupe el espacio restante */
  text-align: right;
  /* Alinea el texto a la derecha */
}

.experiencia-periodo {
  font-size: 0.9em;
  color: #666;
  /* Color de texto más tenue para el periodo */
  margin-bottom: 5px;
}

.experiencia-cargo {
  font-size: 1.2em;
  color: #333;
  /* Color de texto más oscuro para el cargo */
  margin-top: 0;
  margin-bottom: 0;
}

.text-gray-800 {
  --tw-text-opacity: 1;
  color: #FFFFFF;
}

/* Media Queries agrupadas */

/* Moviles (Pantallas pequeñas, hasta 767px) */
@media (max-width: 767px) {

  /* Agregando el responsivo para las secciones experiencia */
  .container-experiencia {
    width: 100%;
    padding: 1;
    margin-top: 1rem;
    /* margen a lo alto */
    line-height: 2.5rem;
    /* espaciado entre los parrafos del texto */
    font-size: small;
    flex-direction: column;
  }

  .tarjeta-experiencia {
    flex-direction: column;
    /* Apila el logo y el contenido en pantallas pequeñas */
    text-align: center;
    /* Centra el texto cuando está apilado */
  }

  .experiencia-logo {
    margin-bottom: 15px;
    /* Espacio debajo del logo cuando está apilado */
    width: auto;
  }

  .experiencia-contenido {
    text-align: center;
    /* Centra el texto cuando está apilado */
  }
}

/* Tablets (Pantallas medianas, entre 768px y 1023px) */
@media (min-width: 768px) and (max-width: 1023px) {

  /* Agregando el responsivo para la seccion experiencia*/
  .container-experiencia {
    width: 100%;
  }

  .tarjeta-experiencia {
    flex-direction: column;
    /* Apila el logo y el contenido en pantallas pequeñas */
    text-align: center;
    /* Centra el texto cuando está apilado */
  }

  .experiencia-logo {
    margin-bottom: 15px;
    /* Espacio debajo del logo cuando está apilado */
  }

  .experiencia-contenido {
    text-align: center;
    /* Centra el texto cuando está apilado */
  }
}

/* Escritorio (Pantallas anchas, a partir de 1024px) */
@media (min-width: 1024px) {

  /* Agregando el responsivo para la seccion experiencia*/
  .container-experiencia {
    width: 100%;
  }
}
</style>
