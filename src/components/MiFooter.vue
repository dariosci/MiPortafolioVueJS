<script setup>
const iconos = import.meta.glob('../assets/icons/*', { eager: true, import: 'default', query: '?url' });

const redesSociales = [
  { id: 1, name: 'instagram', src: iconos['../assets/icons/instagram.svg'], url: 'https://www.instagram.com/darioscili/' },
  { id: 2, name: 'facebook', src: iconos['../assets/icons/facebook.svg'], url: 'https://www.facebook.com/darioscili/' },
  { id: 3, name: 'whatsapp', src: iconos['../assets/icons/whatsapp.svg'], url: 'https://wa.me/542622660229/' },
  { id: 4, name: 'twitter', src: iconos['../assets/icons/twitter.svg'], url: 'https://x.com/darosc' },
  { id: 5, name: 'linkedin', src: iconos['../assets/icons/linkedin.svg'], url: 'https://www.linkedin.com/in/dario-scilipoti-279121254/' },
  { id: 6, name: 'github', src: iconos['../assets/icons/github.svg'], url: 'https://github.com/dariosci/' },
];

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  });
};
</script>

<template>
  <footer class="footer">
    <div class="footer-inner">
      <div class="footer-center">
        <p class="copyright">
          Dario Scilipoti &copy; 2025 Todos los derechos reservados
        </p>
        <div class="redes-sobremi">
          <li v-for="red in redesSociales" :key="red.id">
            <a :href="red.url" target="_blank">
              <img class="icon" :src="red.src" width="35rem" :alt="red.name" />
            </a>
          </li>
        </div>
      </div>

      <button class="btn-top" @click="scrollToTop" aria-label="Volver arriba">
        ↑
      </button>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  position: relative;
  text-align: center;
  color: #fafafa;
  background-color: rgb(94, 94, 94);
  padding: 20px 0;
  width: 100%;
  margin: 0;
}

.footer-inner {
  position: relative;
  display: flex;
  justify-content: center; /* centra el contenido principal */
  align-items: center;
}

.footer-center {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.copyright {
  color: white;
  margin: 0;
}

.redes-sobremi {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;
  margin-top: 0.5rem;
}

.icon {
  width: 2rem;
  height: 2rem;
  margin: 0.25rem;
  transition: all 0.3s;
  cursor: pointer;
}

.icon:hover {
  box-shadow: 0 0 10px #808080;
}

/* === Botón “↑” alineado a la derecha y centrado verticalmente === */
.btn-top {
  position: absolute;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  background-color: #333;
  color: white;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  font-size: 1.3rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-top:hover {
  background-color: #555;
  transform: translateY(-50%) scale(1.1);
}

@media (max-width: 768px) {
  .btn-top {
    right: 10px;
    width: 35px;
    height: 35px;
    font-size: 1.1rem;
  }
}
</style>
