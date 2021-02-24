<template>
  <div class="wrapper">
    <Header />
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
  padding: 5rem 0;
  /*
  border-left: solid red 1px;
  border-right: solid red 1px;
  */
}
</style>
