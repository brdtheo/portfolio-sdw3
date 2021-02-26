<template>
  <section class="section-container">
    <h1>{{ title }}</h1>
    <div class="shadow radius">
      <p v-if="type == 1">
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Asperiores
        perspiciatis perferendis illum rerum non facere dolorem, voluptatibus
        animi at quia reiciendis distinctio voluptas, hic blanditiis dolor nemo
        id ducimus harum!
      </p>
      <ul v-else-if="type == 2">
        <li class="radius" v-for="(repo, i) in repos" :key="i">
          {{ repo.name }}
        </li>
      </ul>
      <p v-else-if="type == 3">
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

div,
p {
  font-family: "Inter", sans-serif;
  font-size: 1.7rem;
  line-height: 1.6;
}

div {
  background: #fff;
  border: solid var(--white) 1px;
  padding: 2rem;
}

ul {
  display: grid;
  row-gap: 2rem;
}

li {
  list-style: none;
  background: var(--grey);
  color: var(--green);
  padding: 0.4rem 1.6rem;
  min-height: 10rem;
}
</style>
