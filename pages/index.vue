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
          text: "About me",
          to: "about",
          sectionType: 1
        },
        {
          text: "Work",
          to: "work",
          sectionType: 2
        },
        {
          text: "Experience",
          to: "experience",
          sectionType: 3
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
