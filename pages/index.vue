<template>
  <div class="wrapper">
    <Header :internalLinks="internalLinks" />
    <main>
      <Section
        v-for="(e, i) in internalLinks"
        :key="i"
        :title="e.text"
        :id="e.to"
        :repos="repositories"
        :type="e.sectionType"
      />
    </main>
  </div>
</template>

<script>
import TOKEN from "~/token";
import Header from "~/components/Header";
import Section from "~/components/Section";

export default {
  components: { Header, Section },

  data() {
    return {
      internalLinks: [
        {
          text: "Infos",
          to: "about",
          sectionType: 1
        },
        {
          text: "Réalisations",
          to: "work",
          sectionType: 2
        },
        {
          text: "Expérience",
          to: "experience",
          sectionType: 3
        },
        {
          text: "Compétences",
          to: "skills",
          sectionType: 4
        }
      ],

      repositories: []
    };
  },

  created() {
    const vm = this;
    var GitHub = require("github-api");

    var gh = new GitHub({
      token: TOKEN
    });

    var me = gh.getUser("brdtheo");
    me.listRepos(function(err, repos) {
      repos.forEach(e => {
        if (!e.private && !e.archived && e.owner.login == "brdtheo") {
          vm.repositories.push(e);
        }
      });
    });
  },

  head() {
    return {
      title: "Théo Billardey - Student & Front End web developer"
    };
  }
};
</script>

<style scoped>
.wrapper {
  max-width: 768px;
  margin: 0 auto;
  padding: 5rem 0;
}

main {
  padding-top: 10rem;
}
</style>
