<script setup>
import { ref, onMounted } from "vue"

const isOpen = ref(false)
const activeSection = ref("#sobre-mi") // sección activa por defecto

const navegacion = ref([
  { id: 1, nombre: 'Sobre Mi', enlace: '#sobre-mi' },
  { id: 2, nombre: 'Educación', enlace: '#estudios' },
  { id: 3, nombre: 'Experiencia', enlace: '#experiencia' },
  { id: 4, nombre: 'Proyectos', enlace: '#proyectos' },
  { id: 5, nombre: 'Habilidades', enlace: '#habilidades' },
  { id: 6, nombre: 'Intereses', enlace: '#intereses' },
  //{ id: 7, nombre: 'Contacto', enlace: '#contacto' }
])

// Detecta el scroll y cambia la sección activa
onMounted(() => {
  const sections = document.querySelectorAll("section[id]")

  window.addEventListener("scroll", () => {
    let current = "#"
    sections.forEach(section => {
      const sectionTop = section.offsetTop - 120 // compensación por el navbar fijo
      if (scrollY >= sectionTop) {
        current = `#${section.id}`
      }
    })
    activeSection.value = current
  })
})
</script>

<template>
  <nav class="navbar" id="mainNav">
    <div class="container nav__container">
      <!-- Logo -->
      <a class="proyectonombre" href="#">
        <span class="titulonavbar">mi</span>
        <span class="titulonavbar2">Portafolio</span>
      </a>

      <!-- Botón hamburguesa -->
      <button
        class="navbar-toggler"
        type="button"
        @click="isOpen = !isOpen"
        :aria-expanded="isOpen.toString()"
        aria-controls="navbarResponse"
        aria-label="Toggle navigation">
        ☰
      </button>

      <!-- Menú -->
      <div id="navbarResponse" class="navbar-menu" :class="{ open: isOpen }">
        <ul class="navbar-nav">
          <a
            v-for="nav in navegacion"
            :key="nav.id"
            :href="nav.enlace"
            class="nav-item nav-link"
            :class="{ active: activeSection === nav.enlace }"
            @click="isOpen = false">
            {{ nav.nombre }}
          </a>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style scoped>
/* Navbar base */
.navbar {
  background-color: #000;
  padding: 0.5rem 1rem;
  z-index: 999;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}

.nav__container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* Logo "miPortafolio" */
.proyectonombre {
  font-size: 1.5rem;
  font-weight: bold;
  text-decoration: none;
}

.titulonavbar {
  color: #fff;
}

.titulonavbar2 {
  color: var(--gold1, #f4bd76);
}

/* Botón hamburguesa */
.navbar-toggler {
  background: none;
  border: none;
  font-size: 1.8rem;
  color: white;
  cursor: pointer;
}

/* Menú */
.navbar-menu {
  display: none;
  flex-direction: column;
  gap: 0.8rem;
  margin-top: 1rem;
  text-align: center;
}

.navbar-menu.open {
  display: flex;
}

/* En desktop */
@media (min-width: 992px) {
  .navbar-menu {
    display: flex !important;
    flex-direction: row;
    align-items: center;
    margin-top: 0;
    gap: 1rem;
  }

  .navbar-toggler {
    display: none;
  }
}

/* Links */
.navbar-nav {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
  padding: 0;
  margin: 0;
}

@media (min-width: 992px) {
  .navbar-nav {
    flex-direction: row;
    gap: 1rem;
  }
}

.nav-link {
  color: white;
  text-decoration: none;
  font-size: 1rem;
  padding-bottom: 4px;
  transition: color 0.3s, border-bottom 0.3s;
}

.nav-link:hover {
  color: var(--gold1, #f4bd76);
}

/* 🔥 Link activo */
.nav-link.active {
  color: var(--gold1, #f4bd76);
  /*border-bottom: 2px solid var(--gold1, #f4bd76);*/
}
</style>
