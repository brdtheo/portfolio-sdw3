<template>
  <section class="section-container">
    <h1>{{ title }}</h1>
    <div class="about-content shadow radius" v-if="type == 1">
      <p>
        Hello 👋
      </p>
      <p>
        I'm Théo Billardey, a 20 years old student in web development. I'm
        currently working on the
        <a class="badge" :href="links.mim.url" :title="links.mim.title">
          {{ links.mim.text }}
        </a>
        project with Meteor, Vue and Quasar. I'm also working on side projects
        that you can discover below involving interesting frameworks and
        libraries. You can also take a look at
        <a class="badge" :href="links.codepen.url" :title="links.codepen.title">
          {{ links.codepen.text }}
        </a>
        since i like to build tiny cool interfaces sometimes.
      </p>
      <p>
        I'm planning to sort of master Vue.js in a few years to build awesome
        web apps 🤓<br />
        I'm also interested in UI design since it's very important and it's part
        of the user experience.
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
    <div class="experience-content shadow radius" v-else-if="type == 3">
      <p>
        My experience
      </p>
    </div>
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
          text: "my codepen profile",
          url: "https://codepen.io/theo-billardey",
          title: "brdtheo on codepen"
        }
      },

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

li a:hover {
  background: var(--white-darken);
}

li a p {
  font-size: 1.4rem;
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
