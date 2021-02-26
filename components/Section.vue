<template>
  <section class="section-container">
    <h1>{{ title }}</h1>
    <p>
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Asperiores
      perspiciatis perferendis illum rerum non facere dolorem, voluptatibus
      animi at quia reiciendis distinctio voluptas, hic blanditiis dolor nemo id
      ducimus harum!
    </p>
  </section>
</template>

<script>
export default {
  name: "Section",

  props: {
    title: {
      type: String
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
</style>
