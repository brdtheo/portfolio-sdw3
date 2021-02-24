<template>
  <div class="wrapper">
    <header />
  </div>
</template>

<script>
import Header from "~/components/Header";

export default {
  components: { Header }
};
</script>

<style scoped>
.wrapper {
  max-width: 768px;
  margin: 0 auto;

  border: solid red 1px;
}
</style>
