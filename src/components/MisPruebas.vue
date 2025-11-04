<template>
  <div class="blob-container"></div>
</template>

<style scoped>
/* Contenedor del efecto */
.blob-container {
  position: absolute; /* posiciona el contenedor de forma absoluta respecto al primer padre posicionado */
  inset: 0;           /* shorthand para top:0; right:0; bottom:0; left:0; — lo estira a todo el contenedor padre */
  width: 100%;        /* asegura ancho completo del contenedor padre */
  height: 100%;       /* asegura alto completo del contenedor padre */
  z-index: 0;         /* lo coloca detrás de elementos con z-index mayor */
  /* Patrón de puntos/retícula (radial gradient usado como "dot pattern") */
  background-image: radial-gradient(
    circle at 50% 50%, /* centro del gradiente */
    #0000 0,           /* color transparente desde 0px */
    #0000 2px,         /* sigue transparente hasta 2px */
    hsl(0 0% 4%) 2px   /* en 2px empieza un gris muy oscuro para formar el punto */
  );
  background-size: 8px 8px; /* tamaño repetido del patrón: controla densidad de los puntos */
  overflow: hidden;         /* oculta contenido que sobresalga del borde del contenedor */
}

/* Capa superior con máscara y rotación (se superpone al patrón) */
.blob-container::after {
  content: "";                    /* genera el pseudo-elemento vacío */
  position: absolute;             /* posicionado respecto a .blob-container */
  inset: 0;                       /* ocupa todo el área del contenedor */
  z-index: 1;                     /* se sitúa por encima del patrón base */
  backdrop-filter: hue-rotate(90deg); /* rota los matices (hue) del contenido de fondo visible detrás */
  mask: linear-gradient(45deg, #0000, #000); /* máscara degradada: permite ver parcialmente el fondo */
  animation: rotaty 5s linear infinite; /* anima la rotación continuamente (definida en @keyframes rotaty) */
  transform-origin: center;       /* origen de la transformación (rotación) en el centro */
}

/* Capa inferior con blobs difusos y animados (aparece detrás del patrón) */
.blob-container::before {
  content: "";   /* genera pseudo-elemento vacío */
  position: absolute; /* posicionado respecto a .blob-container */
  inset: -8em;        /* se extiende más allá de los bordes para que el blur no corte */
  z-index: -1;        /* lo coloca por detrás del patrón base */
  --f: blur(7em) brightness(5); /* variable CSS que contiene filtros aplicados en animaciones */
  --c: #09f;          /* variable con color de referencia (no usada directamente, sirve para ajustar) */

  /* doble animación:
     - blobs-1e28bd3d: mueve lentamente las posiciones de los gradientes (150s)
     - thingy: aplica hue-rotate dentro del filtro (5s) */
  animation:
    blobs-1e28bd3d 150s linear infinite,
    thingy 5s linear infinite;

  background-color: #000; /* color base detrás de las manchas (negro) */

  /* múltiples gradientes elípticos que generan las manchas ("blobs") de color */
  background-image:
    radial-gradient(ellipse 66px 50px at 50% 50%, #0f0 0%, transparent 100%),
    radial-gradient(ellipse 77px 60px at 50% 50%, #0f0 0%, transparent 100%),
    radial-gradient(ellipse 78px 100px at 50% 50%, #0f0 0%, transparent 100%),
    radial-gradient(ellipse 73px 96px at 50% 50%, #0f0 0%, transparent 100%),
    radial-gradient(ellipse 76px 77px at 50% 50%, #0f0 0%, transparent 100%),
    radial-gradient(ellipse 66px 51px at 50% 50%, #0f0 0%, transparent 100%),
    radial-gradient(ellipse 90px 57px at 50% 50%, #0f0 0%, transparent 100%),
    radial-gradient(ellipse 89px 93px at 50% 50%, #0f0 0%, transparent 100%);

  /* tamaño independiente para cada gradiente anterior:
     define la escala de cada "blob" en px para variar la apariencia */
  background-size:
    72px 57px,
    124px 45px,
    87px 116px,
    69px 87px,
    91px 55px,
    115px 34px,
    101px 83px,
    31px 97px;
}

/* Animación 'thingy' — aplica el filtro definido en --f y rota el hue */
@keyframes thingy {
  0% {
    filter: var(--f) hue-rotate(0deg); /* aplica blur/brightness y hue inicial */
  }
  to {
    filter: var(--f) hue-rotate(1turn); /* rota el hue 360 grados al finalizar */
  }
}

/* Animación 'blobs-1e28bd3d' — mueve las posiciones de los gradientes a lo largo del tiempo */
@keyframes blobs-1e28bd3d {
  0% {
    background-position:
      27px 47px,  /* posición inicial del gradiente 1 */
      6px 29px,   /* posición inicial del gradiente 2 */
      6px 86px,   /* ... y así sucesivamente */
      55px 41px,
      3px 39px,
      107px 22px,
      40px 79px,
      7px 26px;
  }
  to {
    background-position:
      -149px -297px, /* posición final muy desplazada para crear movimiento suave */
      311px 111px,
      -200px 89px,
      116px -39px,
      -127px 124px,
      -93px 294px,
      955px 215px,
      94px 905px;
  }
}

/* Animación 'rotaty' — rota el pseudo-elemento ::after (la máscara superior) */
@keyframes rotaty {
  0% {
    transform: rotate(0deg);    /* inicio sin rotación */
  }
  to {
    transform: rotate(360deg);  /* rota completamente (gira continuamente) */
  }
}
</style>
