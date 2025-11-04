<script setup>
  import NavBar from "./components/NavBar.vue";
  import MisDatos from "./components/MisDatos.vue";
  import MisEstudios from "./components/MisEstudios.vue";
  //import MiContacto from "./components/MiContacto.vue";
  import MiExperiencia from "./components/MiExperiencia.vue";
  import MisProyectos from "./components/MisProyectos.vue";
  import MisHabilidades from "./components/MisHabilidades.vue";
  import MisIntereses from "./components/MisIntereses.vue";
  import MiFooter from "./components/MiFooter.vue";
  //import Pruebas from "./components/MisPruebas.vue";

</script>

<template>
  <nav>
    <NavBar></NavBar>
  </nav>
  <header>

  </header>
  <main>
    <MisDatos/>
    <MisEstudios/>
    <MiExperiencia/>
    <MisProyectos/>
    <MisHabilidades/>
    <section id="intereses" class="intereses">
      <h2 class="text-4xl font-bold text-center text-white mb-12">Intereses</h2>
      <MisIntereses/>
    </section>
    <!-- <Pruebas/> -->
    <!--<MiContacto/>-->
  </main>
  <footer>
    <MiFooter/>
  </footer>
</template>

<style scoped>

section h2 {
  margin-top: 32px;
}

</style>
