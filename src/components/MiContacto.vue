<script setup>

</script>

<template>
  <section id="contacto" class="contacto">
    <div class="container">
      <div container class="categoria border-bottom">
        <div class="categoria_icono">
          <!--<i class="fa-solid fa-message"></i>-->
          <h2 class="text-4xl font-bold text-center text-gray-800 mb-12">Contacto</h2>
        </div>
      </div>
      <div class="formulario-contacto">
        <iframe
          src="https://docs.google.com/forms/d/e/1FAIpQLSfIbYAGh2i5TTnNefAVmUYnOkiTRQaZHL6VnZRNRhABcLHm5g/viewform?embedded=true"
          width="auto" height="auto" frameborder="0" marginheight="0" marginwidth="0">Cargando…</iframe>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contacto {
  display: flex;
  justify-content: center;
  /* esto centra el elemento */
  margin-top: 2rem;
  padding: 1rem;
  background-color: var(--fondo-contacto);
  text-align: center;
}

.contacto h2 {
  margin-top: 20px;
}

iframe {
  border: none;
  width: 85rem;
  height: 100rem;
}

.text-gray-800 {
  --tw-text-opacity: 1;
  color: #FFFFFF;
}

/* Media Queries agrupadas */
@media (max-width: 767px) {
  .contacto {
    display: contents;
    width: 100%;
    padding: 1rem;
    margin-top: 1rem;
    /* margen a lo alto */
    line-height: 2.5rem;
    /* espaciado entre los parrafos del texto */
    font-size: small;
  }

  iframe {
    border: none;
    width: 20rem;
    height: 100rem;
  }
}

/* Tablets (Pantallas medianas, entre 768px y 1023px) */
@media (min-width: 768px) and (max-width: 1023px) {
  iframe {
    border: none;
    width: 40rem;
    height: 85rem;
  }
}

/* Escritorio (Pantallas anchas, a partir de 1024px) */
@media (min-width: 1024px) {
  iframe {
    border: none;
    width: 60rem;
    height: 84rem;
  }
}
</style>
