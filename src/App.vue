<template>
  <div id="app">
    <header>
      <nav>
        <h1>My Portfolio</h1>
        <div class="menu-icon" @click="toggleMenu">
          <div class="bar"></div>
          <div class="bar"></div>
          <div class="bar"></div>
        </div>
        <ul :class="{ 'open': isMenuOpen }">
          <li><a href="#about" @click="closeMenu">About</a></li>
          <li><a href="#projects" @click="closeMenu">Projects</a></li>
          <li><a href="#contact" @click="closeMenu">Contact</a></li>
        </ul>
      </nav>
    </header>
    <section id="about" class="section">
      <h2>About Me</h2>
      <p>Hello! I am a web developer with a passion for creating beautiful and functional websites.</p>
    </section>
    <section id="projects" class="section">
      <h2>Member</h2>
      <div v-if="loading">Loading Members...</div>
      <div v-else>
        <div v-for="project in projects" :key="project" class="project">
          <h3>{{ project.first_name }} {{ project.last_name }}</h3>
          <p>{{ project.email }}</p>
          <img v-bind:src="project.avatar">
        </div>
      </div>
    </section>
    <section id="contact" class="section">
      <h2>Contact</h2>
      <p>If you'd like to get in touch, please email me at <a href="mailto:example@example.com">example@example.com</a>.</p>
    </section>
    <footer>
      <p>&copy; 2024 My Portfolio</p>
    </footer>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "App",
  data() {
    return {
      isMenuOpen: false,
      projects: [],
      loading: true
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
    closeMenu() {
      this.isMenuOpen = false;
    },
    fetchProjects() {
      axios.get('https://reqres.in/api/users')
        .then(response => {
          this.projects = response.data.data;
          this.loading = false;
        })
        .catch(error => {
          console.error("There was an error fetching the projects!", error);
          this.loading = false;
        });
    }
  },
  mounted() {
    this.fetchProjects();
  }
};
</script>

<style scoped>
/* 기본 스타일 */
body {
  font-family: 'Arial', sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f0f4f8;
}

#app {
  text-align: center;
}

/* 헤더 스타일 */
header {
  background-color: #007BFF;
  color: white;
  padding: 1rem;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
}

nav h1 {
  margin: 0;
}

nav ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  display: flex;
}

nav li {
  margin: 0 1rem;
}

nav a {
  color: white;
  text-decoration: none;
  font-weight: bold;
}

/* 메뉴 아이콘 스타일 */
.menu-icon {
  display: none;
  flex-direction: column;
  cursor: pointer;
}

.menu-icon .bar {
  width: 25px;
  height: 3px;
  background-color: white;
  margin: 4px 0;
}

/* 모바일 메뉴 스타일 */
@media (max-width: 768px) {
  nav ul {
    flex-direction: column;
    position: absolute;
    top: 100%;
    right: 0;
    background-color: #007BFF;
    width: 100%;
    display: none;
    text-align: left;
  }
  
  nav ul.open {
    display: flex;
  }

  nav li {
    margin: 1rem 0;
  }
  
  .menu-icon {
    display: flex;
  }
}

/* 섹션 스타일 */
.section {
  padding: 2rem;
  margin: 2rem 0;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* 프로젝트 스타일 */
.project {
  margin: 1rem 0;
}

.project h3 {
  margin: 0.5rem 0;
}

/* 푸터 스타일 */
footer {
  background-color: #007BFF;
  color: white;
  padding: 1rem;
}

/* 반응형 디자인 */
@media (max-width: 768px) {
  nav ul {
    flex-direction: column;
  }
  
  nav li {
    margin: 0.5rem 0;
  }
}
</style>
