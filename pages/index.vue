<template>
  <div class="wrapper">
    <Header :internalLinks="internalLinks" />
    <main>
      <Section v-for="(e, i) in internalLinks" :key="i" :title="e.text" />
    </main>
  </div>
</template>

<script>
import Header from "~/components/Header";
import Section from "~/components/Section";

export default {
  components: { Header, Section },

  data() {
    return {
      internalLinks: [
        {
          text: "About me",
          to: "#about"
        },
        {
          text: "Work",
          to: "#work"
        },
        {
          text: "Experience",
          to: "#experience"
        }
      ]
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
