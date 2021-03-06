<template>
  <section class="section-container">
    <h1>{{ title }}</h1>
    <div class="about-content shadow radius" v-if="type == 1">
      <p>
        Bonjour 👋
      </p>
      <p>
        Je suis Théo Billardey, un étudiant de 20 ans en développement web. Je
        travaille actuellement sur
        <a class="badge" :href="links.mim.url" :title="links.mim.title">
          {{ links.mim.text }}
        </a>
        avec Meteor, Vue et Quasar. Je travaille aussi sur des projets en
        parrallèle avec des frameworks et librairies intéressantes que vous
        pouvez découvrir en dessous. Vous pouvez aussi allez voir
        <a class="badge" :href="links.codepen.url" :title="links.codepen.title">
          {{ links.codepen.text }}
        </a>
        puisqu'il m'arrive de réaliser quelques fois de petites interfaces.
      </p>
      <p>
        Il est prévu que je maîtrise Vue.js dans quelques années pour construire
        de superbes applis web 🤓<br />
        Je suis également intéressé par le UI design qui est très important et
        qui prend place dans l'expérience utilisateur.
      </p>
    </div>
    <ul class="repos-content shadow radius" v-else-if="type == 2">
      <li class="radius" v-for="(repo, i) in repos" :key="i">
        <a :href="repo.html_url">
          <h2>{{ repo.name }}</h2>
          <span class="badge-sm">{{ repo.language }}</span>
          <p>{{ repo.description }}</p>
        </a>
      </li>
    </ul>
    <ul class="experience-content shadow radius" v-else-if="type == 3">
      <li class="radius" v-for="(e, i) in experience" :key="i">
        <div class="main-infos radius">
          <h2>
            <span>{{ e.jobTitle }}</span>
            <span class="experience-date">{{ e.date }}</span>
          </h2>
          <p class="experience-location">{{ e.location }}</p>
          <div class="experience-stack">
            <span class="badge-sm" v-for="(s, a) in e.stack" :key="a">
              {{ s }}
            </span>
          </div>
          <p>{{ e.description }}</p>
        </div>
      </li>
    </ul>
    <div class="experience-content shadow radius" v-else-if="type == 4">
      <ul class="skills-grid">
        <li class="skill radius" v-for="(s, i) in skills" :key="i">
          <div class="skill-logo">
            <img
              :src="require(`~/assets/logos/${s.logo}`)"
              :alt="`${s.name} logo`"
            />
          </div>
          <a class="radius-small" :href="s.link">{{ s.name }}</a>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "Section",

  props: {
    title: {
      type: String
    },
    repos: {
      type: Array
    },
    type: {
      type: Number
    }
  },

  data() {
    return {
      links: {
        mim: {
          text: "@madeinmenu",
          url: "https://github.com/madeinmenu",
          title: "Visit made in menu on GitHub"
        },
        codepen: {
          text: "mon profil codepen",
          url: "https://codepen.io/theo-billardey",
          title: "brdtheo on codepen"
        }
      },

      experience: [
        {
          jobTitle: "Développeur front end",
          date: "Juin 2020 - Aujourd'hui",
          description:
            "Contribution au développement d'une application mobile pour gérer des menus. Gestion des données en temps réel, ajout de librairies comme i18n, chart.js et manipulation d'APIs comme Stripe, Mapbox et OpenWeather.",
          location: "Made in Menu - Reims, France",
          stack: [
            "Meteor",
            "Vue",
            "Quasar",
            "Bootstrap",
            "jQuery",
            "Git",
            "mongoDB"
          ]
        },
        {
          jobTitle: "Intégrateur web",
          date: "Janvier 2020",
          description:
            "Refonte d'un site internet d'une association. Utilisation de librairie de translate.js (jQuery) et de GitKraken avec un projet sous MVC et mySQL pour le back end.",
          location: "Il était une fois.. a.s.b.l - Gasperich, Luxembourg",
          stack: ["HTML", "SASS", "jQuery", "Git"]
        },
        {
          jobTitle: "Technicien de maintenance",
          date: "2015-2018",
          description:
            "Création de prototypes de sites internet, première utilisation d'Ubuntu et découverte du monde de la programmation à travers un stage de 11 semaines réparties sur 3 années. Le service informatique du CHT est composé de plusieurs équipes que j'ai eu la chance d'assister et qui m'ont expliqué les bases de leur métiers.",
          location: "Centre Hospitalier de Troyes - Troyes, France",
          stack: ["HTML", "CSS"]
        }
      ],

      skills: [
        {
          name: "Vue",
          link: "https://vuejs.org/",
          logo: "vue.webp"
        },
        {
          name: "Meteor",
          link: "https://www.meteor.com/",
          logo: "meteor.png"
        },
        {
          name: "Svelte",
          link: "https://svelte.dev/",
          logo: "svelte.png"
        },
        {
          name: "Firebase",
          link: "https://firebase.google.com/",
          logo: "firebase.png"
        },
        {
          name: "MongoDB",
          link: "https://www.mongodb.com/",
          logo: "mongodb.png"
        },
        {
          name: "Git",
          link: "https://git-scm.com/",
          logo: "git.png"
        }
      ]
    };
  }
};
</script>

<style scoped>
section {
  margin-bottom: 5rem;
}

section:last-of-type {
  margin-bottom: 0;
}

h1 {
  font-family: "Merriweather", serif;
  font-size: 4.2rem;
  line-height: 1;
  margin-bottom: 1.8rem;
}

h2 {
  font-family: "Merriweather", serif;
  font-weight: 700;
  font-size: 1.8rem;
  line-height: 1;
  margin-bottom: 0.8rem;
}

.about-content,
.repos-content,
.experience-content {
  font-family: "Inter", sans-serif;
  font-size: 1.7rem;
  line-height: 1.6;
  background: #fff;
  border: solid var(--white) 1px;
  padding: 2rem;
}

p {
  margin-bottom: 1.8rem;
}

p:last-of-type {
  margin-bottom: 0;
}

.underline {
  text-decoration: underline;
}

ul {
  display: grid;
  row-gap: 2rem;
}

li {
  overflow: hidden;
  list-style: none;
}

.repos-content li a {
  display: inherit;
  background: var(--white);
  padding: 1.8rem 1.6rem;
  min-height: 10rem;
  transition: background-color ease-in 130ms;
}

.repos-content li a:hover {
  background: var(--white-darken);
}

.repos-content li a p,
.experience-content li p {
  font-size: 1.4rem;
}

.experience-content li {
  background: var(--white);
  padding: 1.8rem 1.6rem;
  min-height: 10rem;
}

.experience-content h2 {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.4rem;
}

.experience-location {
  margin-bottom: 0.8rem;
}

.experience-date {
  font-size: 1.5rem;
}

.experience-content .main-infos {
  display: flex;
  flex-direction: column;
}

.experience-stack {
  display: flex;
  grid-gap: 0.6rem;
  margin: 0.6rem 0 0.4rem;
}

.skills-grid {
  grid-template-columns: repeat(6, 1fr);
  column-gap: 2rem;
}

.skills-grid li {
  padding: 1rem;
  display: grid;
  align-content: space-between;
  grid-template-columns: 100%;
  grid-template-rows: 40px;
  gap: 1.4rem;
  background: var(--white);
}

.skills-grid li img {
  height: 100%;
}

.skill-logo {
  display: flex;
  justify-content: center;
}

.skills-grid li a {
  font-size: 1.4rem;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 40px;
  background: var(--green);
  color: var(--white);
  transition: background-color ease-in 130ms;
}

.skills-grid li a:hover {
  background: var(--green-darken);
}
</style>
