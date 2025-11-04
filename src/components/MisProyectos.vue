<script setup>
import { ref } from 'vue';
// Importar todas las imágenes de la carpeta
const images = import.meta.glob('../assets/images/*', { eager: true, import: 'default', query: '?url' });

const proyectosList = ref([]);
proyectosList.value = [
  { id: 0,
    imagen: images['../assets/images/proyectos.jpg'],
    titulo: 'Página Hospital',
    descripcion: 'Página del Hospital Grl. Las Heras bajo portal Joomla',
    githubLink: 'https://github.com/dariosci/',
    url: 'https://hosplasheras.mendoza.gov.ar/'
  },
  { id: 1,
    imagen: images['../assets/images/proyectos.jpg'],
    titulo: 'Proyecto Final Android',
    descripcion: 'Proyecto Final Integrador - Desarrollo de Aplicaciones Móviles - Argentina Programa 4.0',
    githubLink: 'https://github.com/dariosci/ProyectoFinalAndroid?tab=readme-ov-file#proyecto-final-integrador---desarrollo-de-aplicaciones-m%C3%B3viles---argentina-programa-40/',
    url: 'https://developer.android.com/studio?gad_source=1&gad_campaignid=21831783795&gbraid=0AAAAAC-IOZm5hEjrCTxjGnkQe-KeL9fkv&gclid=CjwKCAjwx8nCBhAwEiwA_z__0wXY7DSN1sbweDND7gpTR_mnN5N3ZmU1HgNDWfQWjv2yKIncPp4v8RoCngIQAvD_BwE&gclsrc=aw.ds&hl=es-419/'
  },
  { id: 2,
    imagen: images['../assets/images/proyectos.jpg'],
    titulo: 'miPortafolio-web',
    descripcion: 'Mi primer portafolio-web creado para la materia Programación I',
    githubLink: 'https://github.com/dariosci/ProyectoFinalAndroid?tab=readme-ov-file#proyecto-final-integrador---desarrollo-de-aplicaciones-m%C3%B3viles---argentina-programa-40/',
    url: 'https://developer.android.com/studio?gad_source=1&gad_campaignid=21831783795&gbraid=0AAAAAC-IOZm5hEjrCTxjGnkQe-KeL9fkv&gclid=CjwKCAjwx8nCBhAwEiwA_z__0wXY7DSN1sbweDND7gpTR_mnN5N3ZmU1HgNDWfQWjv2yKIncPp4v8RoCngIQAvD_BwE&gclsrc=aw.ds&hl=es-419/'
  },
  { id: 2,
    imagen: images['../assets/images/proyectos.jpg'],
    titulo: 'Proyecto 4',
    descripcion: 'Ejemplo de proyecto',
    githubLink: 'https://github.com/dariosci/',
    url: 'https://google.com/'
  },

];
</script>

<template>
  <section id="proyectos" class="proyectos">
    <div class="container">
      <div class="categoria_icono">
        <h2 class="text-4xl font-bold text-center text-gray-800 mb-12">Proyectos</h2>
      </div>
      <div class="galeria">
        <li class="proyecto" v-for="proyecto in proyectosList" :key="proyecto.id">
          <!-- Imagen del proyecto desde el arreglo -->
          <img :src="proyecto.imagen" :alt="proyecto.titulo">
          <div class="proyecto-info">
            <!-- Título y descripción del proyecto utilizando interpolación de Vue.js -->
            <h3>{{ proyecto.titulo }}</h3>
            <p>{{ proyecto.descripcion }}</p>
            <div class="proyecto-links">
              <a :href="proyecto.url" class="btn-ver-mas" target="_blank" rel="noopener noreferrer">Ver
                Proyecto</a>
              <a :href="proyecto.githubLink" class="github-link" target="_blank" rel="noopener noreferrer">Ver
                Código en GitHub</a>
            </div>
          </div>
        </li>

      </div>
    </div>
  </section>
</template>

<style scoped>
.proyectos {
  display: flex;
  justify-content: center;
  padding: 2rem;
  margin-top: 32px;
}

.text-gray-800 {
  --tw-text-opacity: 1;
  color: #FFFFFF;
}

.galeria {
  /* Sombra suave para darle profundidad */
  padding: 20px;
  /* Espaciado interno */
  margin-bottom: 20px;
  /* Espacio entre tarjetas */
  gap: 20px;
  /* Espacio entre el logo y el contenido (Flexbox gap) */
  flex-wrap: wrap;
  /* Permite que los elementos se envuelvan en pantallas pequeñas */
  min-height: 300px;
  background: linear-gradient(270deg, #ff6ec4, #7873f5, #42e695, #fbc1cc);
  background-size: 800% 800%;
  animation: gradientAnimation 15s ease infinite;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 12px;
  align-items: stretch;
}

@keyframes gradientAnimation {
  0% {
    background-position: 0% 50%;
  }

  50% {
    background-position: 100% 50%;
  }

  100% {
    background-position: 0% 50%;
  }
}

/* La clase 'proyecto' es el contenedor individual de cada proyecto */
.proyecto {
  /* Utiliza flexbox para organizar el contenido del proyecto en una columna */
  display: flex;
  /* Establece la dirección de los elementos en columna */
  flex-direction: column;
  /* Aplica un borde de 2px sólido y color gris claro (#ddd) alrededor del proyecto */
  border: 2px solid #ddd;
  /* Redondea las esquinas del contenedor */
  border-radius: 8px;
  /* Oculta cualquier contenido que se desborde del contenedor */
  overflow: hidden;
  /* Establece un color de fondo claro para el proyecto */
  background-color: #f9f9f9;
  /* Define el ancho máximo del proyecto en 222px */
  max-width: 222px;
  /* Hace que el contenedor se ajuste flexiblemente ocupando al menos 300px de ancho */
  flex: 1 1 300px;
  justify-content: space-between; /* Empuja elementos para ocupar todo el alto */
}

/* Estilo para las imágenes dentro del contenedor 'proyecto' */
.proyecto img {
  /* Hace que la imagen ocupe el 100% del ancho del contenedor */
  width: 100%;
  /* Mantiene la relación de aspecto de la imagen */
  height: auto;
  /* Asegura que la imagen se muestre como un bloque, sin espacio en línea alrededor */
  display: block;
}

/* La clase 'proyecto-info' contiene la información del proyecto */
.proyecto-info {
  /* Agrega un padding de 15px alrededor de la información */
  padding: 15px;
  /* Centra el texto dentro del contenedor */
  text-align: center;
  flex-grow: 1; /* Hace que el contenido ocupe el espacio disponible y empuje los botones */
  display: flex;
  flex-direction: column;
  justify-content: space-between; /* Esto mantiene título y descripción arriba, botones abajo */
}

/* Estilo para los títulos de los proyectos */
.proyecto-info h3 {
  /* Establece un margen superior e inferior de 10px */
  margin: 10px 0;
  /* Define el tamaño de la fuente a 1.3em (relativo al tamaño de fuente del contenedor) */
  font-size: 1.3em;
  /* Aplica un color gris oscuro (#333) al texto */
  color: #333;
}

/* Estilo para los párrafos de los proyectos */
.proyecto-info p {
  /* Establece un margen superior e inferior de 10px */
  margin: 10px 0;
  /* Define el tamaño de la fuente a 1em (igual al tamaño de fuente base) */
  font-size: 1em;
  /* Aplica un color gris (#666) al texto */
  color: #666;
}

/* La clase 'proyecto-links' organiza los enlaces y botones del proyecto */
.proyecto-links {
  /* Utiliza flexbox para organizar los enlaces en una columna */
  display: flex;
  /* Establece la dirección de los elementos en columna */
  flex-direction: column;
  /* Establece un espacio de 10px entre los elementos */
  gap: 10px;
  /* Agrega un margen superior de 10px */
  margin-top: 30px;

}

/* Estilo para el botón 'Ver Más' dentro de la clase 'proyecto-links' */
.proyecto-links .btn-ver-mas {
  /* Aplica un color de fondo azul (#007BFF) */
  background-color: #007BFF;
  /* Aplica un color de texto blanco */
  color: #fff;
  /* Agrega un padding de 10px en vertical y 15px en horizontal */
  padding: 10px 15px;
  /* Redondea las esquinas del botón */
  border-radius: 5px;
  /* Elimina el subrayado del texto */
  text-decoration: none;
  /* Aplica una transición suave al cambiar el color de fondo */
  transition: background-color 0.3s;
  margin-top: 1rem;
}

/* Estilo para cuando el botón 'Ver Más' es hover */
.proyecto-links .btn-ver-mas:hover {
  /* Cambia el color de fondo a un azul más oscuro (#0056b3) */
  background-color: #0056b3;
}

/* Estilo para el enlace a GitHub dentro de la clase 'proyecto-links' */
.proyecto-links .github-link {
  /* Aplica un color gris oscuro (#333) al texto */
  color: #333;
  /* Elimina el subrayado del texto */
  text-decoration: none;
  /* Establece el tamaño de fuente a 0.9em (un poco más pequeño que el tamaño base) */
  font-size: 0.9em;
}

/* Estilo para cuando el enlace a GitHub es hover */
.proyecto-links .github-link:hover {
  /* Añade un subrayado al texto */
  text-decoration: underline;
}
</style>
