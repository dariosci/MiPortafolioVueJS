<script setup>
import { ref } from 'vue'
const langSkillsList = ref([]);
const frameSkillsList = ref([]);
const softSkillsList = ref([]);
const bdSkillsList = ref([]);
const idiomasSkillsList = ref([]);

langSkillsList.value = [
  { id: 1, icono: '/src/assets/icons/python.svg', nombre: 'Python', nivel: 4 },
  { id: 2, icono: '/src/assets/icons/js.svg', nombre: 'JavaScript', nivel: 4 },
  { id: 3, icono: '/src/assets/icons/java.svg', nombre: 'Java', nivel: 3 },
  { id: 4, icono: '/src/assets/icons/html.svg', nombre: 'HTML', nivel: 5 },
  { id: 5, icono: '/src/assets/icons/css.svg', nombre: 'CSS', nivel: 4 },
  { id: 6, icono: '/src/assets/icons/sql.svg', nombre: 'SQL', nivel: 4 },
];

frameSkillsList.value = [
  { id: 1, icono: '/src/assets/icons/vuejs.svg', nombre: 'Vue.js', nivel: 4 },
  { id: 2, icono: '/src/assets/icons/nodejs.svg', nombre: 'Node.js', nivel: 4 },
  { id: 3, icono: '/src/assets/icons/bootstrap.svg', nombre: 'Bootstrap', nivel: 3 },
  { id: 4, icono: '/src/assets/icons/react.svg', nombre: 'React.js', nivel: 5 },
  { id: 5, icono: '/src/assets/icons/django.svg', nombre: 'Django', nivel: 4 },
  { id: 6, icono: '/src/assets/icons/flutter.svg', nombre: 'Flutter', nivel: 4 },
];

softSkillsList.value = [
  { id: 1, icono: '/src/assets/icons/git.svg', nombre: 'Git', nivel: 4 },
  { id: 2, icono: '/src/assets/icons/docker.svg', nombre: 'Docker', nivel: 5 },
  { id: 3, icono: '/src/assets/icons/vscode.svg', nombre: 'VSCode', nivel: 5 },
  { id: 4, icono: '/src/assets/icons/photoshop.svg', nombre: 'Photoshop', nivel: 5 },
  { id: 5, icono: '/src/assets/icons/mysql.svg', nombre: 'Workbench', nivel: 4 },
];

bdSkillsList.value = [
  { id: 1, icono: '/src/assets/icons/mongodb.svg', nombre: 'MongoDB', nivel: 4 },
  { id: 2, icono: '/src/assets/icons/mysql2.svg', nombre: 'MySQL', nivel: 4 },
  { id: 3, icono: '/src/assets/icons/mssql.svg', nombre: 'MS SQL', nivel: 3 },
  { id: 4, icono: '/src/assets/icons/postgresql.svg', nombre: 'PSQL', nivel: 5 },
  { id: 5, icono: '/src/assets/icons/mariadb.svg', nombre: 'MariaDB', nivel: 4 },
];

idiomasSkillsList.value = [
  { id: 1, icono: '/src/assets/icons/arg.svg', nombre: 'Español', nivel: 5 },
  { id: 2, icono: '/src/assets/icons/eeuu.svg', nombre: 'Inglés', nivel: 3 },
];
</script>

<template>
  <section id="habilidades" class="proyectos">
    <div class="container">
      <div class="categoria_icono">
        <h2 class="text-4xl font-bold text-center text-gray-800 mb-12">Habilidades - Skills</h2>
      </div>
      <div class="d-flex flex-column fill-height justify-center align-center text-white">
        <div class="skills-categoria">
          <h3>Lenguajes de Programación</h3>
          <ul class="skills">
            <li class="skill" v-for="langSkill in langSkillsList" :key="langSkill.id">
              <!-- Imagen del proyecto desde el arreglo -->
              <img :src="langSkill.icono" :alt="langSkill.nombre">
              <span>{{ langSkill.nombre }}</span> <v-rating v-model="langSkill.nivel" readonly :length="5" :size="21"
                color="yellow-darken-3"></v-rating>
            </li>
          </ul>
        </div>
        <div class="skills-categoria">
          <h3>Frameworks y Librerias</h3>
          <ul class="skills">
            <li class="skill" v-for="frameSkill in frameSkillsList" :key="frameSkill.id">
              <!-- Imagen del proyecto desde el arreglo -->
              <img :src="frameSkill.icono" :alt="frameSkill.nombre">
              <span>{{ frameSkill.nombre }}</span> <v-rating v-model="frameSkill.nivel" readonly :length="5" :size="21"
                color="yellow-darken-3"></v-rating>
            </li>
          </ul>
        </div>
        <div class="skills-categoria">
          <h3>Herramientas y Software</h3>
          <ul class="skills">
            <li class="skill" v-for="softSkills in softSkillsList" :key="softSkills.id">
              <!-- Imagen del proyecto desde el arreglo -->
              <img :src="softSkills.icono" :alt="softSkills.nombre">
              <span>{{ softSkills.nombre }}</span> <v-rating v-model="softSkills.nivel" readonly :length="5" :size="21"
                color="yellow-darken-3"></v-rating>
            </li>
          </ul>
        </div>
        <div class="skills-categoria">
          <h3>Base de Datos</h3>
          <ul class="skills">
            <li class="skill" v-for="bdSkills in bdSkillsList" :key="bdSkills.id">
              <!-- Imagen del proyecto desde el arreglo -->
              <img :src="bdSkills.icono" :alt="bdSkills.nombre">
              <span>{{ bdSkills.nombre }}</span> <v-rating v-model="bdSkills.nivel" readonly :length="5" :size="21"
                color="yellow-darken-3"></v-rating>
            </li>
          </ul>
        </div>
        <div class="skills-categoria">
          <h3>Idiomas</h3>
          <ul class="skills">
            <li class="idiomaskill" v-for="idiomasSkills in idiomasSkillsList" :key="idiomasSkills.id">
              <!-- Imagen del proyecto desde el arreglo -->
              <img :src="idiomasSkills.icono" :alt="idiomasSkills.nombre">
              <span>{{ idiomasSkills.nombre }}</span> <v-rating v-model="idiomasSkills.nivel" readonly :length="5"
                :size="21" color="yellow-darken-3"></v-rating>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.habilidades {
  display: flex;
  justify-content: center;
  padding: 2rem;
  margin-top: 32px;
}

.skill {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  gap: 10px;
  padding: 1rem;
  flex: 1 1 200px;
  max-width: 250px;
  min-height: 80px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);

  /* TRANSICIÓN SUAVE */
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

/* EFECTO AL PASAR EL MOUSE */
.skill:hover {
  transform: translateY(-5px) scale(1.05);
  /* se eleva y aumenta un poco */
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  /* sombra más intensa */
  cursor: pointer;
}

.idiomaskill {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  gap: 10px;
  padding: 1rem;
  flex: 1 1 200px;
  max-width: 250px;
  min-height: 80px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* EFECTO AL PASAR EL MOUSE */
.idiomaskill:hover {
  transform: translateY(-5px) scale(1.05);
  /* se eleva y aumenta un poco */
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  /* sombra más intensa */
  cursor: pointer;
}

.idiomaskill img {
  width: 20px;
  height: 20px;
}

.idiomaskill span {
  font-size: 1em;
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

.text-gray-800 {
  color: #FFFFFF;
}

.skills-categoria h3 {
  display: flex;
  margin-top: 20px;
  margin-bottom: 10px;
  font-size: 2em;
  color: rgb(153, 154, 155);
  font-weight: bold;
}

.skills {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
  gap: 20px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 1rem;
  flex: 1 1 250px;
}

.skill {
  display: flex;
  justify-content: center;
  flex-wrap: wrap-reverse;
  align-items: center;
  gap: 10px;
  padding: 0.3rem;
  flex: 1 1 200px;
  max-width: 250px;
}

.skill img {
  width: 20px;
  height: 20px;
}

.skill span {
  font-size: 1em;
}

@media (max-width: 768px) {
  .skills-categoria h3 {
    justify-content: center;
  }

  .skill {
    justify-content: center;
  }
}
</style>
