<template>
  <section class="section-container">
    <h1>{{ title }}</h1>
    <div class="about-content shadow radius" v-if="type == 1">
      <p>
        Hello everyone 👋
      </p>
      <p>
        I'm Théo Billardey and i'm a 20 years old student in web development.
        I'm currently working on the
        <a class="badge" :href="links.mim.url" :title="links.mim.title">
          {{ links.mim.text }}
        </a>
        project with Meteor, Vue and Quasar. I'm also working on side projects
        involving frameworks, libraries that i'm interested in. that you can
        discover below. You can also take a look at
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
        {{ repo.name }}
      </li>
    </ul>
    <div class="experience-content shadow radius" v-else-if="type == 3">
      <p>
        My experience
      </p>
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
      }
    };
  }
};
</script>

<style scoped>
section {
  margin-bottom: 5rem;
}

h1 {
  font-family: "Merriweather", serif;
  font-size: 4.2rem;
  line-height: 1;
  margin-bottom: 1.8rem;
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
  list-style: none;
  background: var(--white);
  padding: 0.4rem 1.6rem;
  min-height: 10rem;
}
</style>
